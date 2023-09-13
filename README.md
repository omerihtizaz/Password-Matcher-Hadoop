# MPI Password Cracker

## Overview

This project implements a parallelized password cracker using MPI (Message Passing Interface). The program reads encrypted passwords and salts from a `shadow.txt` file, distributing the workload across multiple processes for efficient searching. The objective is to uncover the original passwords through brute force techniques.

## Table of Contents

- [Objective](#objective)
- [Methodology](#methodology)
- [Usage](#usage)
- [Dependencies](#dependencies)
- [How to Run](#how-to-run)
- [Contributors](#contributors)
- [License](#license)

## Objective

The goal of this project is to demonstrate the effectiveness of parallel computing in password cracking. It leverages MPI to divide the task among multiple processes, allowing for concurrent searches and significantly reducing the overall time taken.

## Methodology

1. **Parsed Data Retrieval:**
   Encrypted passwords and salts are extracted from `shadow.txt` through a tokenization process, segregating pertinent information.

2. **MPI Initialization:**
   MPI framework is initialized, determining process count and individual ranks for efficient parallelization.

3. **Task Allocation:**
   Workload division is performed based on password length ranges, ensuring equitable distribution across processes.

4. **Master Process (Rank 0):**
   - Solicits user input for a username.
   - Procures corresponding encrypted password and salt from `shadow.txt`.
   - Disseminates salt and encrypted password to all slave processes.

5. **Slave Processes (Ranks > 0):**
   - Receive salt and encrypted password from the master process.
   - Execute password cracking within assigned password length ranges.
   - Signal all processes to halt the search upon finding a password.

6. **Password Cracking Function:**
   - Utilizes a brute force strategy, systematically generating and validating password combinations.
   - Encrypts each password attempt and cross-references it with the provided encrypted password.
   - Returns `true` upon a successful match.

7. **MPI Finalization:**
   Concludes MPI communication post-task completion for synchronization and resource cleanup.

## Usage

To use this password cracker, follow the instructions provided in the [How to Run](#how-to-run) section.

## Dependencies

- MPI (Message Passing Interface)

## How to Run

1. Clone the repository to your local machine.
2. Compile the code with an MPI compiler.
3. Ensure you have a `shadow.txt` file containing the necessary information.
4. Run the executable with appropriate permissions.

## Contributors

- Aleezeh Usman (18I-0529)
- Areesha Tahir (18I-1655)
- Faaira Ahmed (18I-0423)
- Omer Ihtizaz (18I-0404)

## License

[MIT License](LICENSE)
