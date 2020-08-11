# Modeling and Verification of CKB Consensus Protocol against Selfish Mining Attacks

[Nervos Network](https://www.nervos.org) is a two-layer blockchain with Common Knowledge Base (CKB) consensus protocol. The two-step confirmation in the protocol is designed to resist the selfish mining attacks and solve the low throughput problem of traditional blockchains. We provided a formal verification of the two-step confirmation by model checking. In addition, we would like to emphasize the security against the selfish mining attacks. To demonstrate all the verification status and trigger conditions, we used UPPAAL to construct a visualized framework, and all the properties are verified formally with the model checker. With the graphical state flow, UPPAAL can show a clear transition process.

## Preliminaries
### CKB Blockchain
There are two layers in the CKB blockchain. The first layer provides the decentralized infrastructure and it is responsible for settling assets. The second layer is where the transactions generate. [CKB consensus protocol](https://github.com/nervosnetwork/rfcs/tree/master/rfcs) is design for running the first layer without a third-party supervision.

## Requirements
* JAVA SE 13.0.2
* UPPAAL 4.1.24

## Features
* Providing the transaction verification state flow of the CKB consensus protocol.
* Verifying the properties of the transaction verification and the block propagation.
* Proving CKB’s ability to resist selfish mining attacks.

## Variable Declarations
The two-step confirmation is divided into small operations. All the variables mark the outcome of these operations. The variables initially default to zero, and the templates would give the assignments to these variables after each operation. Value 1 and 2 in the assignments denote that an operation succeeds and fails respectively. The variables would be regarded as the guard parameters of the transitions for the next operation.

## Templates
There are five templates in the normal_scenario.xml. twoStep template illustrates the verification states in two-step confirmation. miningNode template provides the behavior of a miner. Users can join CKB blockchain as the full nodes. A full node is in charge of verification and choosing the folk, and its missions are given in the fullNode template. The block propagation mechanism is represented in the blockPropagation template. The initialization template is used for resetting all the variables and clocks.

The model in normal_scenario.xml demonstrates the case that all the miners behave well. There is a case that a malicious group consisting of some dishonest miners intentionally hides blocks and create a secret branch. The malicious group would like to launch a selfish mining attack. This case is presented in the attack_scenario.xml. selfishMining template offers the [selfish mining attack algorithm](https://www.cs.cornell.edu/~ie53/publications/btcProcFC.pdf), which is proposed by Ittay Eyal and Emin Gu ̈n Sirer.

## Simulator
In the simulator view you can observe the control flow of the transaction verification in two-step confirmation. Note that every parameter in the transition guards represent the outcome after completing each operation.


## Verifier
The ability to resist selfish mining attacks and the properties of CKB consensus protocol are listed in CTL formula. You can click the “check” button to see the results of verification.

## Author
Yi-Chun, Feng
Contact me at: yichunfeng@pku.edu.cn

## License
**This is not an open source, all rights are reserved.**
**Any reproduction or distribution is prohibited. Please do not any create derivative works.**
