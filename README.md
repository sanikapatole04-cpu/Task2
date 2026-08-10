# Stock Portfolio Tracker

# Hardcoded stock prices
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOGL": 140,
    "MSFT": 420,
    "AMZN": 180
}

total_investment = 0
portfolio = []

print("=== Stock Portfolio Tracker ===")
print("Available stocks:", ", ".join(stock_prices.keys()))

while True:
    stock = input("\nEnter stock name (or 'done' to finish): ").upper()

    if stock == "DONE":
        break

    if stock not in stock_prices:
        print("Stock not available. Please choose from the given list.")
        continue

    quantity = int(input("Enter quantity: "))

    price = stock_prices[stock]
    investment = price * quantity
    total_investment += investment

    portfolio.append([stock, quantity, price, investment])

    print(f"{stock}: {quantity} shares × ${price} = ${investment}")

# Display portfolio
print("\n=== Portfolio Summary ===")

for item in portfolio:
    print(f"Stock: {item[0]}, Quantity: {item[1]}, "
          f"Price: ${item[2]}, Value: ${item[3]}")

print(f"\nTotal Investment: ${total_investment}")

# Save result to a text file
with open("portfolio.txt", "w") as file:
    file.write("Stock Portfolio Summary\n")
    file.write("-----------------------\n")

    for item in portfolio:
        file.write(
            f"Stock: {item[0]}, Quantity: {item[1]}, "
            f"Price: ${item[2]}, Value: ${item[3]}\n"
        )

    file.write(f"\nTotal Investment: ${total_investment}")

print("\nPortfolio saved successfully to portfolio.txt")
