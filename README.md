# GameGPT

## Overview
GymnasiumAgent is a Python application that serves as an interface between an OpenAI chat model and a Gym environment. It allows you to interact with the environment using natural language and returns the environment's responses in a structured format.

![Python 3.x](https://img.shields.io/badge/python-3.x-blue)
![OpenAI](https://img.shields.io/badge/OpenAI-Chat_Model-green)
![Gym](https://img.shields.io/badge/Gym-Environment-red)
![Tenacity](https://img.shields.io/badge/Tenacity-Retry-yellow)
![dotenv](https://img.shields.io/badge/dotenv-Environment_Variables-purple)

## Features

- **Natural Language Interface**: Interact with the Gym environment using natural language.
- **Tenacity Retry**: Retries the action in case of a `ValueError`.
- **Environment Variables**: Uses `.env` files for environment-specific settings.

## Installation

# Install the required packages
```
git clone https://github.com/tdolan21/GameGPT.git
cd GameGPT
pip install gymnasium openai tenacity python-dotenv
```

## Usage

1. Initialize the Gym environment:

   ```python
    env = gym.make("Blackjack-v1")
   ```

2. Initialize the GymnasiumAgent:

   ```python
    agent = GymnasiumAgent(model=ChatOpenAI(temperature=0.2), env=env)
    ```

3. Reset the agent and get the observation:

```python
    observation, info = env.reset()
    agent.reset()
    obs_message = agent.observe(observation)
    ```

4. Perform actions and get observations:

```python
    while True:
        action = agent.act()
        observation, reward, termination, truncation, info = env.step(action)
        obs_message = agent.observe(observation, reward, termination, truncation, info)
        if termination or truncation:
            break
    ```

5. Close the environment:

```python
    env.close()
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License

[MIT License](LICENSE)

---

For more details, please refer to the comments within the code.
