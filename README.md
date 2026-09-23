# 🚀 Futuristic Temperature Vault (Min Stack)

A custom, high-performance data structure engineered to store high-frequency temperature readings recorded every second and instantly retrieve the absolute minimum recorded value at any given moment in **constant time**.

## 🌍 Real-World Impact
High-frequency telemetry streams like cloud infrastructure tracking, financial market data feeds, and industrial IoT sensor networks depend heavily on real-time aggregation metrics. This system guarantees performance bounds independent of data volume, preventing tracking latency in production monitoring tools.

## ⚙️ Architecture & Logic
Instead of scanning the entire history of temperatures to find the lowest point (which takes O(n) time), this system uses a **Dual-Stack Approach**:
1. **Primary Stack (`stack`)**: Captures every incoming temperature reading sequentially.
2. **Minimum Tracker Stack (`min_stack`)**: Maintains a running record of the minimum value alive at that specific depth.

When a value is dropped (`pop`), the minimum stack mutates concurrently—ensuring the historical minimum state is perfectly preserved without historical traversal.

## 📊 Algorithmic Performance

| Operation | Time Complexity | Space Complexity | Technical Description |
| :--- | :--- | :--- | :--- |
| **`push(x)`** | **O(1)** | O(1) | Adds the temperature to the data array and updates the minimum state. |
| **`pop()`** | **O(1)** | O(1) | Discards the latest stream entry and synchronizes the tracking array. |
| **`top()`** | **O(1)** | O(1) | Peeks at the most recent reading without modification. |
| **`get_min()`** | **O(1)** | O(1) | Instantly accesses the tail of `min_stack` to provide the running minimum. |

## 🛠️ Getting Started

### Prerequisites
- Python 3.8 or higher
- Jupyter Notebook (optional, for step-by-step interactive testing)

### Installation & Execution
1. Clone this repository to your local system:
   ```bash
   git clone https://github.com<your-username>/futuristic-temperature-vault.git
   cd futuristic-temperature-vault
   ```

2. Run the automated testing simulation framework:
   ```bash
   python min_stack.py
   ```

## 🧪 Simulation Sample Output
When executing the simulation script, your console will show dynamic tracking tracking similar to this:

```text
--- Step 1: Ingesting Data Stream ---
📥 Pushed:  42.50°C | ❄️  Current Min:  42.50°C
📥 Pushed: -12.30°C | ❄️  Current Min: -12.30°C
📥 Pushed:  88.10°C | ❄️  Current Min: -12.30°C

--- Step 2: Evicting Data (Pops) ---
📤 Popped:  88.10°C | 🔝 New Top: -12.30°C | ❄️  Current Min: -12.30°C
📤 Popped: -12.30°C | 🔝 New Top:  42.50°C | ❄️  Current Min:  42.50°C
```
