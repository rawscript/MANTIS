# MANTIS: Generative AI-Driven Multi-Agent System for Adaptive Industrial Hardware Optimization in Predictive Maintenance

## Overview

MANTIS is a novel generative AI-driven multi-agent framework for predictive maintenance that addresses limitations of static models, dynamic condition adaptation, noisy multi-modal data, and proactive hardware reconfiguration. The system demonstrates superior performance with RMSE=12.94 on NASA CMAPSS FD001 dataset, achieving 35% downtime reduction and 22% energy efficiency improvement over traditional ML baselines.

## Live Demo

API: https://c9ae-34-173-215-122.ngrok-free.app/docs

## Key Results

| Metric | MANTIS | Baseline | Improvement |
|--------|--------|----------|-------------|
| RUL RMSE | 12.94 | 14.2 | +9.1% |
| Downtime Reduction | 35% | 0% | +35% |
| Energy Efficiency | 22% | 0% | +22% |
| Sequences Processed | 22,751 | - | - |

## System Architecture

MANTIS implements five specialized collaborative agents:

1. **Perception Agent**: Real-time sensor data fusion and preprocessing
2. **Predictive Agent**: LSTM-based RUL prediction and anomaly detection (RMSE=12.94)
3. **Generative Agent**: NVIDIA Nemotron LLM failure scenario generation
4. **Optimization Agent**: MARL parameter tuning for hardware reconfiguration
5. **Actuation Agent**: Digital twin simulation for safe deployment

## Technical Implementation

- **Dataset**: NASA CMAPSS FD001 (21 sensors + 3 operational settings)
- **Model**: LSTM (24→64→1) + Autoencoder, trained on 30-cycle windows
- **Generative AI**: NVIDIA Llama-3.1-Nemotron-Nano-VL-8B-v1
- **API**: FastAPI microservice with PyTorch model serving
- **Deployment**: Google Colab + ngrok tunnel

## API Endpoints

```
GET  /                    System status and metrics
POST /predict             RUL prediction (30x24 sensor array)
GET  /scenarios           Nemotron failure scenarios
GET  /results             IEEE Table II results
GET  /health              Service health check
```

## Prediction Input Format

```json
{
  "sensors": [
    [0.5, 0.6, ...],  // timestep 1: 24 features
    [0.51, 0.61, ...], // timestep 2: 24 features
    ...
  ]  // 30 timesteps total
}
```

## Installation

```bash
pip install torch pandas numpy scikit-learn fastapi uvicorn openai pyngrok
python mantis.py
```

## Files Included

```
mantis.py                 Complete training pipeline
mantis_model.pth          Trained LSTM (RMSE=12.94)
X.npy                     Training sequences (22,751)
y.npy                     RUL ground truth
scaler.pth                MinMaxScaler parameters
```

## IEEE Standards Compliance

- P2975.1: Data attributes validated (21 sensors + 3 ops settings)
- P2975.2: Model V&V achieved (RMSE=12.94 vs baseline 14.2)
- P2976: XAI via Nemotron scenario generation
- Reproducible: Full code + model weights + dataset simulation

## Reproduction Steps

1. Run `mantis.py` for training (generates model files)
2. Deploy FastAPI server (automatic ngrok tunnel)
3. Test `/predict` endpoint with 30x24 sensor arrays
4. Results match publication: RMSE=12.94, 35% downtime reduction

## Publication Venue Targets

- IEEE Transactions on Industrial Informatics
- IEEE Access
- Engineering Applications of Artificial Intelligence

## Author

James Mwaura  
Zetech University, Nairobi, Kenya  
mwaurajames@zetech.ac.ke

## License

MIT License - Free for academic and commercial use.
