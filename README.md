
# 🚀 LunarLander-v3 Policy AI Model

This project creates a pre-trained AI policy for the [LunarLander-v3](https://gymnasium.farama.org/environments/box2d/lunar_lander/) environment using [Gymnasium](https://gymnasium.farama.org/) and NumPy. The policy is stored in a `.npy` file and defines how the lunar lander should behave to safely land on the moon's surface.

---

## 📆 What's Inside

- `pso_best_policy.npy`  
  A NumPy array containing the trained weights of a policy optimized using **Particle Swarm Optimization (PSO)**.

- `pso_evaluate.py`  
  Python script to evaluate the performance of the trained policy over multiple episodes in the LunarLander-v3 environment.

- `policy_module.py` *(you need to include or create this)*  
  A Python module that defines the `policy_action(policy, observation)` function. This function uses the policy to determine the action to take based on the current observation.

- `pso_evaluate.bat`  
  A Windows batch script to run the evaluation with the correct arguments (optional for automation).

---

## ▶️ How to Run

### 1. Install Dependencies

```bash
pip install gymnasium[box2d] numpy
```

Or if using `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 2. Evaluate the Model

```bash
python pso_evaluate.py --filename pso_best_policy.npy --policy_module policy_module
```

This will:

- Run 100 episodes of the LunarLander environment
- Render the first 5 for visual feedback
- Print the **average reward** over all episodes

---

## 🧠 How It Works

- The `.npy` file stores the neural network weights or parameters learned via **Particle Swarm Optimization (PSO)**.
- The `policy_action()` function maps observations (state of the lander) to an action (left, right, up, no-op).
- The script evaluates how well the policy performs by calculating cumulative rewards across multiple trials.

### 🌀 What is PSO?

**Particle Swarm Optimization** is a population-based optimization algorithm inspired by the social behavior of birds and fish. It works by initializing a "swarm" of candidate solutions (particles), each with a position (policy parameters) and velocity. During training:

- Each particle moves through the search space guided by its own best known position and the global best position found by any particle.
- Over time, particles converge toward the best-performing policy.

This method is effective for optimizing black-box functions like policies where gradient information is not available.

---

## 🗪 Example Output

```text
Average reward over 100 episodes: 275.67
```

(A score above 200 is generally considered successful landing behavior in this environment.)

---

## 📁 Folder Structure

```text
lunarLander/
│
├── pso_best_policy.npy         # Trained model parameters
├── pso_evaluate.py             # Evaluation script
├── pso_policy.py               # Contains policy_action(policy, observation)
├── pso_evaluate.bat            # Windows script for running evaluation
├── pso_train.py                # Training model using PSO
```

---

## 📌 Notes

- You must provide a `policy_module.py` file with a function:

```python
def policy_action(policy, observation):
    # Your logic to convert observation and policy into an action
    return action
```

- The action must be one of: `0` (do nothing), `1` (fire left), `2` (fire main engine), or `3` (fire right).

---

## 🙌 Acknowledgements

- OpenAI Gym / Gymnasium for the LunarLander-v3 environment.
