# Banking System - Complete Class Hierarchy

## 📊 Class Hierarchy Overview

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              BANKING SYSTEM ARCHITECTURE                            │
└─────────────────────────────────────────────────────────────────────────────────────┘

```

## 🔗 Interface Hierarchy

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                    INTERFACES                                      │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  ┌─────────────────────┐    ┌─────────────────────┐    ┌─────────────────────┐     │
│  │   AccountOperation  │    │   AccountObserver   │    │   Serializable      │     │
│  │   (Command Pattern) │    │  (Observer Pattern) │    │  (Java Built-in)    │     │
│  └─────────────────────┘    └─────────────────────┘    └─────────────────────┘     │
│           │                           │                           │                 │
│           │                           │                           │                 │
│           ▼                           ▼                           ▼                 │
│  ┌─────────────────────┐    ┌─────────────────────┐    ┌─────────────────────┐     │
│  │   execute()         │    │   update(String)    │    │   writeObject()     │     │
│  │   getDescription()  │    │                     │    │   readObject()      │     │
│  └─────────────────────┘    └─────────────────────┘    └─────────────────────┘     │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

## 🏗️ Abstract Class Hierarchy

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                 ABSTRACT CLASSES                                   │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                           BaseTransaction                                   │   │
│  │                        (Abstract Class)                                    │   │
│  │                                                                             │   │
│  │  ┌─────────────────────────────────────────────────────────────────────┐   │   │
│  │  │                    Properties:                                        │   │   │
│  │  │                    • amount: double                                   │   │   │
│  │  │                    • dateTime: String                                 │   │   │
│  │  │                    • transactionId: String                            │   │   │
│  │  │                                                                       │   │   │
│  │  │                    Methods:                                           │   │   │
│  │  │                    • getTransactionId(): String                       │   │   │
│  │  │                    • getAmount(): double                              │   │   │
│  │  │                    • getDateTime(): String                            │   │   │
│  │  │                    • getType(): String (abstract)                     │   │   │
│  │  │                    • toString(): String                               │   │   │
│  │  └─────────────────────────────────────────────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                    │                                               │
│                                    │ (inherits)                                    │
│                                    ▼                                               │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                              Account                                         │   │
│  │                           (Abstract Class)                                  │   │
│  │                                                                             │   │
│  │  ┌─────────────────────────────────────────────────────────────────────┐   │   │
│  │  │                    Properties:                                        │   │   │
│  │  │                    • userName: String                                 │   │   │
│  │  │                    • accountNumber: int                               │   │   │
│  │  │                    • balance: double                                  │   │   │
│  │  │                    • transactions: List<BaseTransaction>              │   │   │
│  │  │                    • creationDate: String                             │   │   │
│  │  │                                                                       │   │   │
│  │  │                    Methods:                                           │   │   │
│  │  │                    • deposit(double): void                            │   │   │
│  │  │                    • withdraw(double): boolean                        │   │   │
│  │  │                    • transfer(double, Account): boolean               │   │   │
│  │  │                    • canWithdraw(double): boolean (abstract)          │   │   │
│  │  │                    • addInterest(): void (abstract)                   │   │   │
│  │  │                    • getAccountType(): String (abstract)              │   │   │
│  │  │                    • getTransactions(): List<BaseTransaction>         │   │   │
│  │  │                    • getTransactionsByType(String): List<...>         │   │   │
│  │  │                    • getTransactionsByDateRange(LocalDateTime, LocalDateTime): List │   │   │
│  │  └─────────────────────────────────────────────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

## 🏦 Concrete Class Hierarchy

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                 CONCRETE CLASSES                                  │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                        TRANSACTION CLASSES                                  │   │
│  │                                                                             │   │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │   │
│  │  │DepositTransaction│  │WithdrawalTransaction│  │InterestTransaction│              │   │
│  │  │                 │  │                 │  │                 │              │   │
│  │  │• getType():     │  │• getType():     │  │• getType():     │              │   │
│  │  │  "Deposit"      │  │  "Withdrawal"   │  │  "Interest Added"│              │   │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────┘              │   │
│  │                                                                             │   │
│  │  ┌─────────────────┐  ┌─────────────────┐                                   │   │
│  │  │TransferTransaction│  │TransferReceiveTransaction│                                   │   │
│  │  │                 │  │                 │                                   │   │
│  │  │• targetAccountNumber: int│  │• sourceAccountNumber: int│                                   │   │
│  │  │• getType():     │  │• getType():     │                                   │   │
│  │  │  "Transfer to Acc#"│  │  "Received from Acc#"│                                   │   │
│  │  └─────────────────┘  └─────────────────┘                                   │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                          ACCOUNT CLASSES                                     │   │
│  │                                                                             │   │
│  │  ┌─────────────────────────────────────────────────────────────────────┐   │   │
│  │  │                        SavingsAccount                                │   │   │
│  │  │                                                                     │   │   │
│  │  │  Properties:                                                        │   │   │
│  │  │  • INTEREST_RATE: 0.04 (4%)                                         │   │   │
│  │  │  • minimumBalance: 1000                                             │   │   │
│  │  │                                                                     │   │   │
│  │  │  Methods:                                                           │   │   │
│  │  │  • canWithdraw(double): boolean                                     │   │   │
│  │  │  • addInterest(): void                                              │   │   │
│  │  │  • getAccountType(): "Savings"                                      │   │   │
│  │  │  • getMinimumBalance(): double                                      │   │   │
│  │  │  • setMinimumBalance(double): void                                  │   │   │
│  │  └─────────────────────────────────────────────────────────────────────┘   │   │
│  │                                                                             │   │
│  │  ┌─────────────────────────────────────────────────────────────────────┐   │   │
│  │  │                        CurrentAccount                                │   │   │
│  │  │                                                                     │   │   │
│  │  │  Properties:                                                        │   │   │
│  │  │  • overdraftLimit: 10000                                            │   │   │
│  │  │                                                                     │   │   │
│  │  │  Methods:                                                           │   │   │
│  │  │  • canWithdraw(double): boolean                                     │   │   │
│  │  │  • addInterest(): void (no interest)                                │   │   │
│  │  │  • getAccountType(): "Current"                                      │   │   │
│  │  │  • getOverdraftLimit(): double                                      │   │   │
│  │  │  • setOverdraftLimit(double): void                                  │   │   │
│  │  └─────────────────────────────────────────────────────────────────────┘   │   │
│  │                                                                             │   │
│  │  ┌─────────────────────────────────────────────────────────────────────┐   │   │
│  │  │                     FixedDepositAccount                              │   │   │
│  │  │                                                                     │   │   │
│  │  │  Properties:                                                        │   │   │
│  │  │  • INTEREST_RATE: 0.08 (8%)                                         │   │   │
│  │  │  • maturityDate: LocalDateTime                                       │   │   │
│  │  │  • termMonths: int                                                   │   │   │
│  │  │                                                                     │   │   │
│  │  │  Methods:                                                           │   │   │
│  │  │  • canWithdraw(double): boolean (only after maturity)               │   │   │
│  │  │  • addInterest(): void                                              │   │   │
│  │  │  • getAccountType(): "Fixed Deposit (X months)"                     │   │   │
│  │  │  • getMaturityDate(): LocalDateTime                                 │   │   │
│  │  │  • getFormattedMaturityDate(): String                               │   │   │
│  │  └─────────────────────────────────────────────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

## 🏭 Factory & Utility Classes

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                            FACTORY & UTILITY CLASSES                              │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                           AccountFactory                                   │   │
│  │                        (Factory Pattern)                                   │   │
│  │                                                                             │   │
│  │  Static Methods:                                                           │   │
│  │  • createAccount(String, String, int, double): Account                     │   │
│  │    - Creates Savings, Current, or Fixed Deposit accounts                   │   │
│  │    - Handles initial deposit logic                                         │   │
│  │    - Validates account type and parameters                                 │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                     AccountRepository & Friends                            │   │
│  │                             (Gateway)                                      │   │
│  │                                                                             │   │
│  │  Core Operations:                                                          │   │
│  │  • findAllAccounts(): List<Account>                                        │   │
│  │  • findAccount(int): Account                                               │   │
│  │  • saveAccount(Account) / saveAccounts(Collection<Account>)                │   │
│  │  • deleteAccount(int): boolean                                             │   │
│  │                                                                             │   │
│  │  Implementations:                                                          │   │
│  │  • InMemoryAccountRepository – deep-copies aggregates for deterministic    │   │
│  │    tests                                                                   │   │
│  │  • JdbcAccountRepository – persists serialized aggregates into the         │   │
│  │    `accounts` table using JDBC transactions                               │   │
│  │  • MigrationRunner – executes `db/migration` SQL scripts before JDBC usage │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                         BankHttpServer                                     │   │
│  │                       (HTTP Adapter)                                       │   │
│  │                                                                             │   │
│  │  Public Methods:                                                           │   │
│  │  • start(): void                                                           │   │
│  │    - Binds lightweight HTTP server and registers REST contexts             │   │
│  │  • stop(): void                                                            │   │
│  │    - Shuts down contexts and executor                                      │   │
│  │  • getPort(): int                                                          │   │
│  │    - Reports the bound local port                                          │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

## 🎯 Command Pattern Implementation

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                           COMMAND PATTERN CLASSES                                │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                        AccountOperation                                    │   │
│  │                           (Interface)                                      │   │
│  │                                                                             │   │
│  │  Methods:                                                                   │   │
│  │  • execute(): boolean                                                       │   │
│  │  • getDescription(): String                                                │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                    │                                               │
│                                    │ (implements)                                  │
│                                    ▼                                               │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐                      │
│  │DepositOperation │  │WithdrawOperation│  │TransferOperation│                      │
│  │                 │  │                 │  │                 │                      │
│  │• account: Account│  │• account: Account│  │• sourceAccount: Account│                      │
│  │• amount: double │  │• amount: double │  │• targetAccount: Account│                      │
│  │• execute(): boolean│  │• execute(): boolean│  │• amount: double │                      │
│  │• getDescription(): String│  │• getDescription(): String│  │• execute(): boolean│                      │
│  └─────────────────┘  └─────────────────┘  │• getDescription(): String│                      │
│                                            └─────────────────┘                      │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

## 👁️ Observer Pattern Implementation

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                           OBSERVER PATTERN CLASSES                               │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                        AccountObserver                                    │   │
│  │                           (Interface)                                      │   │
│  │                                                                             │   │
│  │  Methods:                                                                   │   │
│  │  • update(String): void                                                    │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                    │                                               │
│                                    │ (implements)                                  │
│                                    ▼                                               │
│  ┌─────────────────┐  ┌─────────────────┐                                          │
│  │ConsoleNotifier  │  │TransactionLogger│                                          │
│  │                 │  │                 │                                          │
│  │• update(String): void│  │• update(String): void│                                          │
│  │  - Prints to console│  │  - Writes to file     │                                          │
│  │  - Real-time notifications│  │  - Persistent logging  │                                          │
│  └─────────────────┘  └─────────────────┘                                          │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

## 🏦 Main System Classes

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                            MAIN SYSTEM CLASSES                                    │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                              Bank                                          │   │
│  │                        (Core System Class)                                 │   │
│  │                                                                             │   │
│  │  Properties:                                                                │   │
│  │  • accounts: Map<Integer, Account>                                          │   │
│  │  • observers: List<AccountObserver>                                         │   │
│  │  • operationQueue: Queue<AccountOperation>                                  │   │
│  │  • executorService: ExecutorService                                         │   │
│  │                                                                             │   │
│  │  Methods:                                                                   │   │
│  │  • createAccount(String, String, double): Account                           │   │
│  │  • closeAccount(int): boolean                                               │   │
│  │  • updateAccountHolderName(int, String): boolean                            │   │
│  │  • getAccount(int): Account                                                 │   │
│  │  • getAllAccounts(): List<Account>                                          │   │
│  │  • getAccountsByType(String): List<Account>                                 │   │
│  │  • searchAccounts(String): List<Account>                                    │   │
│  │  • queueOperation(AccountOperation): CompletableFuture<OperationResult>     │   │
│  │  • executePendingOperations(): void                                         │   │
│  │  • addInterestToAllSavingsAccounts(): int                                   │   │
│  │  • addObserver(AccountObserver): void                                       │   │
│  │  • notifyObservers(String): void                                            │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                             ConsoleUI                                      │   │
│  │                        (User Interface Class)                              │   │
│  │                                                                             │   │
│  │  Properties:                                                                │   │
│  │  • scanner: Scanner                                                         │   │
│  │  • bank: Bank                                                               │   │
│  │  • ANSI color constants                                                     │   │
│  │                                                                             │   │
│  │  Methods:                                                                   │   │
│  │  • start(): void (main UI loop)                                             │   │
│  │  • displayMainMenu(): void                                                  │   │
│  │  • createAccountMenu(): void                                                │   │
│  │  • accountOperationsMenu(): void                                            │   │
│  │  • performDeposit(Account): void                                            │   │
│  │  • performWithdrawal(Account): void                                         │   │
│  │  • performTransfer(Account): void                                           │   │
│  │  • viewTransactions(Account): void                                          │   │
│  │  • generateAccountStatement(Account): void                                  │   │
│  │  • displayAllAccounts(): void                                               │   │
│  │  • searchAccounts(): void                                                   │   │
│  │  • generateReportsMenu(): void                                              │   │
│  │  • accountManagementMenu(): void                                            │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                       BankingApplication                                   │   │
│  │                        (Main Entry Point)                                  │   │
│  │                                                                             │   │
│  │  Methods:                                                                   │   │
│  │  • main(String[]): void                                                     │   │
│  │    - Loads existing bank data                                               │   │
│  │    - Creates ConsoleUI instance                                             │   │
│  │    - Starts the application                                                 │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

## 🔄 Relationships & Dependencies

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                            CLASS RELATIONSHIPS                                   │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  BankingApplication                                                               │
│         │                                                                          │
│         │ creates                                                                  │
│         ▼                                                                          │
│  ConsoleUI ──────────────┐                                                        │
│         │                 │ uses                                                  │
│         │                 ▼                                                       │
│         │           Bank ──────────────┐                                          │
│         │                 │             │ contains                                │
│         │                 │             ▼                                         │
│         │                 │     Account (abstract) ──────────────┐                │
│         │                 │             │                         │                │
│         │                 │             │ extends                 │                │
│         │                 │             ▼                         │                │
│         │                 │  ┌─────────────────┐                  │                │
│         │                 │  │ SavingsAccount  │                  │                │
│         │                 │  │ CurrentAccount  │                  │                │
│         │                 │  │FixedDepositAccount│                  │                │
│         │                 │  └─────────────────┘                  │                │
│         │                 │             │                         │                │
│         │                 │             │ contains                │                │
│         │                 │             ▼                         │                │
│         │                 │  BaseTransaction (abstract) ──────────┘                │
│         │                 │             │                                          │
│         │                 │             │ extends                                  │
│         │                 │             ▼                                          │
│         │                 │  ┌─────────────────────────────────┐                   │
│         │                 │  │ DepositTransaction              │                   │
│         │                 │  │ WithdrawalTransaction           │                   │
│         │                 │  │ InterestTransaction             │                   │
│         │                 │  │ TransferTransaction             │                   │
│         │                 │  │ TransferReceiveTransaction      │                   │
│         │                 │  └─────────────────────────────────┘                   │
│         │                 │                                                       │
│         │                 │ uses                                                  │
│         │                 ▼                                                       │
│         │           AccountFactory                                                │
│         │                                                                          │
│         │ uses                                                                     │
│         ▼                                                                          │
│  AccountRepository ──────┐                                                        │
│         │                 │ uses                                                  │
│         │                 ▼                                                       │
│         │           AccountOperation (interface) ──────────────┐                  │
│         │                 │                                     │                  │
│         │                 │ implements                          │                  │
│         │                 ▼                                     │                  │
│         │  ┌─────────────────┐                                  │                  │
│         │  │DepositOperation │                                  │                  │
│         │  │WithdrawOperation│                                  │                  │
│         │  │TransferOperation│                                  │                  │
│         │  └─────────────────┘                                  │                  │
│         │                                                       │                  │
│         │ uses                                                  │                  │
│         ▼                                                       │                  │
│  AccountObserver (interface) ──────────────┐                    │                  │
│         │                                   │                    │                  │
│         │ implements                        │                    │                  │
│         ▼                                   │                    │                  │
│  ┌─────────────────┐                        │                    │                  │
│  │ConsoleNotifier  │                        │                    │                  │
│  │TransactionLogger│                        │                    │                  │
│  └─────────────────┘                        │                    │                  │
│                                             │                    │                  │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

## 📋 Design Patterns Summary

| Pattern | Purpose | Classes Involved |
|---------|---------|------------------|
| **Factory Pattern** | Create different account types | `AccountFactory` |
| **Observer Pattern** | Notifications and logging | `AccountObserver`, `ConsoleNotifier`, `TransactionLogger` |
| **Command Pattern** | Encapsulate operations | `AccountOperation`, `DepositOperation`, `WithdrawOperation`, `TransferOperation` |
| **Repository Pattern** | Data persistence abstraction | `AccountRepository`, `JdbcAccountRepository`, `InMemoryAccountRepository` |
| **Template Method** | Transaction structure | `BaseTransaction` with abstract `getType()` |
| **Strategy Pattern** | Different withdrawal strategies | `canWithdraw()` in different account types |

## 🎯 Key Features by Class

### **Core Business Logic**
- **Bank**: Central management, account operations, threading
- **Account**: Abstract banking operations, transaction management
- **Account Types**: Specific business rules for each account type

### **Data Management**
- **AccountRepository Implementations**: Persistence layer (in-memory & JDBC)
- **BaseTransaction**: Transaction data structure
- **Transaction Types**: Specific transaction behaviors

### **User Interface**
- **ConsoleUI**: Complete user interface with menus
- **BankingApplication**: Application entry point

### **Reporting Utilities**
- **StatementGenerator**: Builds period-specific account statements with balance summaries.
- **AccountStatement**: Immutable value object encapsulating statement metadata and transactions.
- **StatementPresenter**: Formats statement summaries and transaction listings for the console UI.

### **Design Patterns**
- **AccountFactory**: Object creation
- **AccountObserver**: Event notifications
- **AccountOperation**: Command encapsulation

This hierarchy demonstrates a well-structured, maintainable, and extensible banking system that follows SOLID principles and industry-standard design patterns.
