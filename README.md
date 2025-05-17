# AI-Based Timing Violation Prediction from RTL using Combinational Logic Depth Estimation

## 🔍 Overview

Timing analysis is a crucial part of designing any complex IP/SoC. Traditionally, timing reports are generated after synthesis, which can be a time-consuming process. This can lead to project delays and architectural refactoring if timing violations are detected late.

This project aims to **develop an AI/ML-based algorithm** that predicts the **combinational logic depth** of signals in behavioral RTL, allowing early identification of potential **timing violations**—thus accelerating the design flow and reducing rework.

---

## 🧠 Problem Statement

Build an **AI/ML algorithm** to:
> Predict combinational complexity/depth of signals in RTL designs to quickly identify **timing violations** before synthesis.

---

## 🧾 Definitions

- **Combinational Complexity / Logic Depth:**  
  The number of basic gates (AND/OR/NOT/NAND/etc.) required to generate a signal, typically the input to a flip-flop, from the outputs of other flip-flops through the longest combinational path.

- **Timing Violation:**  
  Occurs when the combinational delay of a signal path is too long to be supported by the target clock frequency, leading to incorrect behavior.

---

## 📥 Inputs

1. RTL module (Behavioral Verilog/VHDL)
2. Signal(s) for which combinational depth is to be predicted
3. Additional feature data (e.g., fan-in, fan-out) from EDA tools

---

## 📤 Output

- Predicted **combinational logic depth** of each signal
- Early warning for **potential timing violations**

---

## 📊 Dataset

- RTL benchmark files (open-source or synthetic)
- Extracted netlist features (gate count, fan-in, path depth)
- Annotated ground truth data for supervised learning

---

## 🛠️ Tools & Technologies

- **Language**: Python, Verilog
- **ML Libraries**: Scikit-learn, PyTorch / TensorFlow
- **EDA Tools**: Yosys / Synopsys Design Compiler (for feature extraction)
- **Parsing Tools**: Pyverilog or HDLParser

---

## 🚀 Approach

1. **Parse RTL** to extract signals and structural data.
2. **Build feature vectors** (e.g., fan-in, operator type, path depth).
3. **Train ML model** (Random Forest, DNN, etc.) on labeled data.
4. **Predict logic depth** of unseen RTL signals.
5. **Flag signals** with depth near critical timing threshold.

---

## 📈 Model Evaluation

- Metrics: Mean Absolute Error (MAE), R² score, Accuracy (for classification models)
- Cross-validation on held-out RTL modules
- Visual comparison with EDA tool-based timing reports

---

## 🧪 Example

```verilog
assign D = (A & B) | C;
D_int = ~D;
always @(posedge Clk)
    Q <= D_int;
