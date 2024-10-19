# UART Transmission System Using FPGA

## Project Overview

This project implements a Universal Asynchronous Receiver/Transmitter (UART) communication system using FPGA (Field Programmable Gate Array) technology. UART is widely used for asynchronous serial communication where only two wires are needed for data transmission and reception. The project incorporates both the transmitter and receiver modules, button debouncing logic, and a full simulation environment with waveforms, schematics, and synthesized designs. It is designed, synthesized, and tested using Xilinx Vivado tools, targeting a Xilinx Artix-7 FPGA platform.

This repository demonstrates a complete end-to-end system, highlighting expertise in FPGA programming, hardware description languages (VHDL), and digital design practices. 

## Features

- **Fully functional UART transmitter and receiver**: Implements both 8-bit serial data transmission and reception.
- **Button debouncing mechanism**: Integrated debounce logic to ensure reliable button press detection.
- **Testbench with simulation**: A comprehensive testbench to simulate and verify UART functionality using Xilinx Vivado’s simulator.
- **FPGA Synthesis and Implementation**: Realized using Xilinx Vivado tools, with detailed schematics and synthesized designs.
- **Constraint and pin mapping**: Defines FPGA pin locations using a constraints file for proper I/O connection.
- **Clear documentation of design flow**: Showcases RTL schematics, synthesized designs, and implementation details.

## Project Components

### 1. UART Transmitter
The UART transmitter takes 8-bit parallel input data, converts it into a serial format, and transmits it over a single wire according to UART protocol (start/stop bits and no parity in this implementation).

- **Features**:
  - Supports standard UART frame format with 8 data bits.
  - Generates start, data, and stop bits sequentially.
  - Handles the serialization of data.
  - Built-in state machine that transitions through IDLE, START, DATA, and STOP states.

### 2. UART Receiver
The UART receiver module reconstructs the 8-bit parallel data from the incoming serial data stream. It identifies start and stop bits and ensures proper framing of data.

- **Features**:
  - Detects start and stop bits.
  - Reads incoming serial data and converts it back to an 8-bit parallel format.
  - State machine implementation for IDLE, START, DATA, and STOP phases.

### 3. Push Button Debouncer
Mechanical buttons often generate multiple transitions when pressed due to bouncing, causing unreliable inputs. This debouncing circuit ensures a clean and stable signal for button presses.

- **Functionality**:
  - Stabilizes noisy signals from mechanical button presses.
  - Provides clean output after filtering unwanted transitions.

### 4. UART Controller (Top-Level Design)
The UART controller integrates the transmitter, receiver, and button debounce modules, managing the control flow and coordinating data transmission and reception.

- **Functionality**:
  - Manages data flow between the transmitter and receiver.
  - Controls the state transitions and timing between different modules.
  - Serves as the top-level module for synthesis and testing.

### 5. Testbench for Simulation
A custom testbench simulates the entire system to verify functionality. The testbench generates the clock, reset, and data signals and checks the output against expected values.

- **Key Features**:
  - Generates test vectors to verify UART transmission and reception.
  - Monitors system response and checks for proper timing and data accuracy.
  - Includes different test scenarios: varying data inputs, reset conditions, and clock cycles.
  - Produces waveform output for detailed analysis of UART operations.

### 6. Constraints (XDC File)
The constraints file maps the design's I/O ports to the physical pins of the FPGA, ensuring that UART transmission, reception, and button control signals are correctly routed to the board.

- **Details**:
  - Defines FPGA pin mappings for UART TX, RX, and button inputs.
  - Includes clock configuration and timing constraints for proper FPGA operation.

## Design Flow

### RTL Schematic
The RTL (Register Transfer Level) schematic generated by Vivado provides an overview of how the different modules are connected logically. This is essential for understanding the flow of data between the UART transmitter, receiver, and controller.


### Synthesized Design
Once the design is synthesized, Vivado maps the design to the FPGA’s physical resources, including logic slices, lookup tables (LUTs), and flip-flops. This is shown in the synthesized design report.


### Implemented Schematic and Design
The implemented schematic shows the actual FPGA resource utilization after placement and routing. This view allows us to verify how the design fits within the available hardware resources and whether it meets timing constraints.

### Testbench Simulation
The testbench simulation is essential for validating the UART transmission system. The following waveform showcases the transmission of 8-bit data (`0x55`) over UART, highlighting the start and stop bits and ensuring that data is transmitted and received accurately.


## Simulation and Testing

The UART system was rigorously tested using Vivado’s built-in simulation environment. Key test cases included:

- **Serial Data Transmission**: Sending `0x55` (binary `01010101`) from the transmitter to the receiver and verifying the correctness of the received data.
- **Start/Stop Bit Detection**: Ensuring that the UART system correctly identifies the start and stop bits and reads data only during the DATA phase.
- **Idle State Handling**: Verifying that the transmitter and receiver both enter the IDLE state when no data is being transmitted.
- **Debounced Button Input**: Checking that button presses are correctly debounced and do not generate multiple signals.

### Waveform Analysis
The simulation shows proper timing and functionality of the UART protocol. The transitions between the start, data, and stop bits can be observed and validated in the waveform output, ensuring that the system operates within expected parameters.

## How to Run the Project

### Prerequisites

- Xilinx Vivado (version 2020.2 or later)
- Xilinx FPGA development board (e.g., Artix-7)
- Basic understanding of VHDL and digital design principles

### Instructions

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-repository/UART_FPGA_Project.git
   cd UART_FPGA_Project
   ```

2. **Open in Vivado**: 
   - Launch Xilinx Vivado and open the project folder.
   - The design includes the top-level module, UART controller, and the testbench for simulation.

3. **Synthesize and Implement**:
   - Synthesize the design using Vivado’s synthesis tool.
   - Implement the design and check for timing constraints and resource utilization.

4. **Run Simulation**:
   - Simulate the design using the provided testbench. Use Vivado’s waveform viewer to verify the correct transmission and reception of data.

5. **Generate Bitstream and Program FPGA**:
   - After successful synthesis and implementation, generate the bitstream and program your FPGA board to test the design in real-time.

## Hardware Platform

This design targets a Xilinx FPGA platform, specifically the Artix-7 FPGA. The project uses Vivado for the design, simulation, and synthesis processes, ensuring high-performance implementation on FPGA hardware.

- **FPGA Board**: Xilinx Artix-7 FPGA (or compatible device)
- **Development Tools**: Xilinx Vivado Design Suite

## Future Enhancements

Some potential areas for enhancement in future iterations of this project:

1. **Baud Rate Configurability**: Add support for configuring the UART baud rate dynamically.
2. **Parity Bit for Error Detection**: Implement parity bits to enable basic error detection during data transmission.
3. **FIFO Buffers**: Introduce FIFO buffers for smoother handling of high-speed data transmission.
4. **Support for Additional Protocols**: Extend the design to support SPI or I2C communication protocols alongside UART.

## Conclusion

This project demonstrates an in-depth understanding of UART communication and FPGA-based digital design. By implementing the UART protocol, debouncing logic, and testbench simulation, the project showcases a robust and scalable approach to hardware communication systems. The design has been fully tested and validated using Xilinx Vivado, ensuring that it meets industry standards for FPGA-based communication systems.
