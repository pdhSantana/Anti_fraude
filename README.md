# Anti_fraude
Modelo de detecção de fraude em financiamentos de veículo

O modelo proposto tem como objetivo ter uma precisão elevada, porém que ainda consiga classificar uma boa quantidade de casos.

Para a criação do modelo foi feita uma bateria de testes, dentre eles vou escolher os mais importantes.

|    #     | OneHotEncoder | Eliminando coluans com 80% dos dados nulos | XGBoost ou LightGbm | Smote Borderlinde | Treinando modelo com o dataset completo |
|----------|---------------|--------------------------------------------|---------------------|-------------------|-----------------------------------------|                     
| Teste 1  |      ✅       |                 ✅                        |       XGBoost       |       ❌          |                   ✅                   |
| Teste 2  |      ✅       |                 ❌                        |       XGBoost       |       ❌          |                   ✅                   |
| Teste 3  |      ✅       |                 ✅                        |       XGBoost       |       ❌          |                   ❌                   |
| Teste 4  |      ✅       |                 ❌                        |       XGBoost       |       ❌          |                   ❌                   |

Fiz os testes com smote também, porém o modelo não se saiu tão bem quanto nos demais, por isso estão todos desmarcados.
Os treinos com o dataset completo foi usando o Kfold estratificado que iria me garanti que o modelo iria sempre treinar com folds que continham os targets ( que estavam extremamente desbalanceado).
Os sem está com o dataset completo foi usando apenas 80% para treino ( com o KFold estratificado também) e os 20% para teste/validação. Porém ele não teve um desempenho tão bom quanto o acima.

Tunei os parâmetros dos modelos com optuna fiz treinos separados com foco em precisão e em AUPRCS. Certo momento tentei treinar com foco em precisão e recall mas não deu certo, o optuna não consigo otimizar muito bem os parâmetros.

Após o tunagem, peguei os parâmetros do Teste 1 e Teste 3 e validei como documentado no código


