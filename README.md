## Descrição do projeto:
Este projeto demonstra como controlar um display SSD1306 e LEDs RGB usando um joystick e o microcontrolador Raspberry Pi Pico. O código foi escrito em C e utiliza o Pico SDK para configurar módulos como GPIO, I2C e PWM.

## Funcionalidades

1. Controle do Display SSD1306:

  - Configura a comunicação I2C para controlar o display.

  - Renderiza gráficos no display com base na posição do joystick.

  - Limpa e atualiza o display periodicamente.

2. Controle dos LEDs RGB:

  - Configura o PWM para controlar a intensidade dos LEDs RGB.

  - Ajusta a cor dos LEDs com base na posição do joystick.

  - Habilita e desabilita os slices PWM utilizando botões.

3. Debounce dos Botões:

  - Configura GPIOs para leitura dos botões.

  - Implementa debounce de botões utilizando alarmes.

## Requisitos de Hardware:
Para implementar o projeto de controle do display SSD1306 e LEDs RGB com o Raspberry Pi Pico, você precisará dos seguintes componentes de hardware:

1. Raspberry Pi Pico:

  - Microcontrolador RP2040 com suporte a programação em C/C++ utilizando o Pico SDK.

2. Display SSD1306:

  - Um display OLED com comunicação I2C.

3. LEDs RGB:

  - LEDs RGB com pinos separados para cada cor (vermelho, verde, azul).

4. Joystick:

  - Um joystick analógico.

5. Botões:

 - Botões para interações.

 - Protoboard e Jumpers:

 - Uma protoboard para montar o circuito.

 - Jumpers para conectar os componentes ao Raspberry Pi Pico.

6. Fonte de Alimentação:

 - Cabo USB para alimentação do Raspberry Pi Pico e programação.

7. Resistores (opcional):

 - Resistores podem ser necessários para limitar a corrente que passa pelos LEDs RGB.

## Conexões do Display SSD1306:

- Pino SDA do Display: Conectar ao GPIO correspondente do Raspberry Pi Pico.

- Pino SCL do Display: Conectar ao GPIO correspondente do Raspberry Pi Pico.

- Pino de Alimentação (VCC) do Display: Conectar ao VCC (3.3V ou 5V) do Raspberry Pi Pico.

- Pino de Terra (GND) do Display: Conectar ao GND do Raspberry Pi Pico.

## Conexões dos LEDs RGB:
- Pino da Cor Vermelha (R) do LED RGB: Conectar ao GPIO 12 do Raspberry Pi Pico.

- Pino da Cor Verde (G) do LED RGB: Conectar ao GPIO 13 do Raspberry Pi Pico.

- Pino da Cor Azul (B) do LED RGB: Conectar ao GPIO 14 do Raspberry Pi Pico.

- Pino de Terra (GND) do LED RGB: Conectar ao GND do Raspberry Pi Pico.

## Conexões do Joystick:

- Pino X do Joystick: Conectar a um pino ADC do Raspberry Pi Pico.

- Pino Y do Joystick: Conectar a outro pino ADC do Raspberry Pi Pico.

- Pino de Sinal do Botão do Joystick: Conectar ao GPIO correspondente do Raspberry Pi Pico.

- Pino de Terra (GND) do Joystick: Conectar ao GND do Raspberry Pi Pico.

## Conexões dos Botões:

- Pino de Sinal dos Botões: Conectar aos GPIOs correspondentes do Raspberry Pi Pico.

- Pino de Terra (GND) dos Botões: Conectar ao GND do Raspberry Pi Pico.

## Instalação do Pico SDK:

- Siga as instruções no Guia de Configuração do Pico SDK.

## Configuração do CMakeLists.txt:

- Certifique-se de que o arquivo CMakeLists.txt esteja configurado corretamente para incluir as bibliotecas necessárias:
"
cmake_minimum_required(VERSION 3.13)
include(pico_sdk_import.cmake)

project(display_leds_project)

pico_sdk_init()

add_executable(display_leds main.c)

target_link_libraries(display_leds pico_stdlib hardware_pwm hardware_i2c)

pico_enable_stdio_usb(display_leds 1)
pico_enable_stdio_uart(display_leds 0)

pico_add_extra_outputs(display_leds) "

## Funções

1. init_btns:

- Configura os pinos GPIO para os botões e habilita as interrupções com debounce.

2. init_leds:

- Configura os pinos PWM para os LEDs RGB e inicializa os slices PWM.

3. init_display:

- Configura a comunicação I2C para o display SSD1306 e inicializa o display.

4. init_joystick_adc:

- Configura os pinos ADC para leitura do joystick.

5. update_display:

- Atualiza o display com base na posição do joystick.

6. update_pwm:

- Atualiza os níveis de PWM dos LEDs RGB com base na posição do joystick.

7. debounce:

- Implementa debounce para os botões utilizando alarmes.

## Código Principal (main)

- Inicializa os módulos e periféricos necessários (botões, LEDs, display, joystick).

- Em loop, lê os valores do joystick, atualiza o PWM dos LEDs e renderiza o display.

## Executando o Projeto:

- Conecte o Raspberry Pi Pico ao computador usando um cabo USB.

- Compile e carregue o código no Raspberry Pi Pico.

- Observe o display SSD1306 exibindo gráficos com base na posição do joystick e os LEDs RGB mudando de cor conforme o movimento do joystick.