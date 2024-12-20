# EarthStream Milestone 3

## Introduction

- **Milestone 1 code:** [GitHub Repository](https://github.com/nuwrldnf8r/esp32_dfinity_agent)  
- **Milestone 2 code:** [GitHub Repository](https://github.com/nuwrldnf8r/earthstream_milestone2)

Since Milestone 2, our focus has been on field testing, refining our sensor code, working on housings, and addressing hardware-related challenges. We are now ready to initiate a presale and establish a few projects. Consequently, this milestone has pivoted slightly from a data marketplace to a **presale marketplace**, aligning with our current product journey.

This milestone consists of the following components:

## Sensor Presale

A dedicated **canister module** enables us to:  
- Sell sensors and track presale progress.  
- Accept various cryptocurrencies as payment (via ChainFusion).  
- Assign sensors to projects.  

**Key Feature:**  
Users can either:  
1. Purchase sensors for personal use.  
2. Allocate sensors to projects, earning credits generated by the sensor data.

## Projects

A canister for managing projects, enabling users to:  
- Create and list projects.  
- Search for projects by name, ownership (e.g., "My Projects"), tag, status (for admin purposes), or votes.  
- Vote for projects.

## Images

A simple canister designed to store images uploaded for projects.

## Front-End

The front-end brings all the components together into a **marketplace interface**. It enables users to:  
- View and vote on projects.  
- Assign sensors to projects.  
- Purchase and track sensors.  

**Future Enhancements:**  
- Display sensor data and credits once sensors are deployed.  

Additionally, the front-end includes an **admin dashboard** for tracking sensor sales, approving projects, and other administrative tasks.

## Challenges and Lessons Learned

### Payment Module Iteration  
Initially, we developed a canister module to handle:  
- Payments from multiple chains.  
- Multi-signature (multisig) functionality for accessing funds.

**Issue:**  
This approach proved to be **too expensive in terms of cycles**.

**Solution:**  
The current module leverages **ChainFusion** to validate transactions via the `eth_getTransactionByHash` RPC call using a dedicated EVM RPC canister. This allows us to:  
- Verify that an amount was sent from a specific contract address/chain to a target address.  
- Minimize cycle consumption, as cycles are only used for confirmed transactions.  

**Note:**  
- Payments are routed to a **Gnosis-style safe** that handles multisig.  
- The module currently supports **EVM chains only**.
