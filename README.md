# JAVA_LCA_2
68_Zubair_Shaikh



class Account {
    private final String accountNumber;
    private double balance;

    Account(String accountNumber, double openingBalance) {
        if (openingBalance < 0) {
            throw new IllegalArgumentException(
                "Opening balance cannot be negative"
            );
        }

        this.accountNumber = accountNumber;
        this.balance = openingBalance;
    }

    void deposit(double amount) {
        validateAmount(amount);
        balance += amount;
    }

    boolean withdraw(double amount) {
        validateAmount(amount);

        if (amount > balance) {
            return false;
        }

        balance -= amount;
        return true;
    }

    double checkBalance() {
        return balance;
    }

    String getAccountNumber() {
        return accountNumber;
    }

    private void validateAmount(double amount) {
        if (amount <= 0) {
            throw new IllegalArgumentException(
                "Amount must be positive"
            );
        }
    }
}


    public static void main(String[] args) {

        Account savings = new Account("ACC1001", 1000.00);
        Account current = new Account("ACC1002", 500.00);

        savings.deposit(250.00);
        savings.withdraw(100.00);

        current.deposit(300.00);
        current.withdraw(150.00);

        printBalance(savings);
        printBalance(current);
    }

    private static void printBalance(Account account) {
        System.out.printf(
            "%s balance: %.2f%n",
            account.getAccountNumber(),
            account.checkBalance()
        );
    }
}