# AleoJS
> EthersJS (+Hardhat) for the Aleo ecosystem

AleoJS library aims to be a simple and compact library for interacting with the Aleo blockchain and its ecosystem. It’ll fully leverage the existing tools and provide an easy to use interface to anyone who wants to build on top of Aleo.

## Installation and Setup

1. Clone the current repository
```sh
git clone git@github.com:venture23-zkp/aleojs.git
```

2. Move inside the repository
```sh
cd aleojs
```

2. Install the necessary packages
```sh
npm install
```

3. Build the project
```sh
npm run build
```

4. Install the project globally
```sh
npm install -g .
```

To check if the installation is successful, try running `aleojs-dev` command.

The expected output is the following:
```
Using shell: /bin/zsh
     _    _                _ ____  
    / \  | | ___  ___     | / ___| 
   / _ \ | |/ _ \/ _ \ _  | \___ \ 
  / ___ \| |  __/ (_) | |_| |___) |
 /_/   \_\_|\___|\___/ \___/|____/ 
                                   
Usage: index [options] [command]

AleoJS CLI

Options:
  -V, --version   output the version number
  -h, --help      display help for command

Commands:
  init            Initialize your AleoJS project
  add [options]   Add a new component or resource
  compile         Compile your AleoJS project
  run             Run your AleoJS project
  help [command]  display help for command
```

> Incase the `aleojs-dev` is not found or there is some issue, replace `aleojs-dev` with `node <LOCATION-TO-ALEOJS>/dist/index.js`.

Example:
```sh
node ../aleojs/dist/index.js init demo
```

## How to use aleojs-dev
1. Initialize the project 

    To kickstart your project with AleoJS-Dev, simply run the following command, replacing project_name with your desired project name:
    ```sh
    aleojs-dev init project_name
    ```

    This command generates a boilerplate template for your project, which includes essential folders such as programs for writing contracts, scripts for interacting with contracts, and tests for testing your contracts.

2. Add another contract in project

    Should you wish to add another contract to your project, use the following command, replacing contract_name with the name of your contract:
    ```sh
    aleojs-dev add contract_name
    ```

    This command will add a new contract to the programs folder.


3. Compile the contracts
    Compile your contracts by running the following command:
    ```sh
    aleojs-dev compile 
    ```
    This command compiles the contract(s) inside the programs folder. Generate four different files after parsing the leo file.

    types.ts: Contains Aleo and TypeScript-specific types and schemas.

    leo2js.ts: Provides conversion logic from Leo to TypeScript.

    js2leo.ts:Offers conversion logic from TypeScript to Leo.

    main.ts:Creates functions used for interacting with Aleo.

4. Run test scripts for contract

    To test your contracts, run the following command:
    ```sh
    aleojs-dev run test 
    ```

    This command executes the test files inside the tests folder.

5. Deploy contract

    To deploy your contract, run the following command:
    ```sh
    aleojs-dev deploy [program_name] --network [network_name]
    ```


## Example
Let's walk through a quick example to illustrate the process.

1. Initialize a new project named "token" with the following command

    ```sh
    aleojs-dev init token
    ```
    This will create a new directory named "token" with all necessary structure for your project along with sample leo file.

2. Add a new contract to your project named "token" using this command:
    ```sh
    aleojs-dev add token
    ```
    This creates a token.leo file inside the programs folder. For now, lets get the code for token.leo from leo workshop github. You can obtain sample token.leo code from the Leo Workshop GitHub repository __[here](https://github.com/AleoHQ/workshop/blob/master/token/src/main.leo)__
3. Compile your contracts by running:
    ```sh
    aleojs-dev compile
    ```
    This compiles the contracts inside the programs folder, generating TypeScript types and conversion logic files.

4. To run tests for your contract, add a test file named token.js to the tests folder. Include the following code in the test file:
    
    ```
    import { mint_private } from "../artifacts/js/token";

    test("mint private", async () => {
      expect(
        await mint_private(
          "aleo1uwuxqnhkg9wsmqvsfjdm3jqsevx4fgme2ml405sgduc66d4cpc8swkn28j",
          BigInt(2)
        )
      );
    });
    ```
5. Finally, run your tests with this command:
    ```sh
    aleojs-dev run test
    ```
    This will run our token.js

6. At last we deploy contract
    ```sh
    aleojs-dev deploy token --network testnet
    ```
