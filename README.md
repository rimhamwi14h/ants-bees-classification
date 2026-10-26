# Ants vs Bees — Image Classification

Classification d’images de fourmis et d’abeilles par transfert
d’apprentissage avec PyTorch et ResNet18.

## Objectif

Adapter un réseau préentraîné à une classification binaire,
puis évaluer ses performances et analyser ses erreurs.

## Technologies

Python, PyTorch, torchvision, scikit-learn, Matplotlib et Jupyter.

## Données

Dataset Hymenoptera :
- Entraînement : 244 images.
- Validation : 153 images.
- Classes : ants et bees.

Les données sont placées dans :
`data/hymenoptera_data/train/` et `data/hymenoptera_data/val/`,
avec un sous-dossier par classe.

## Méthode

- Redimensionnement, recadrage à 224 × 224 et normalisation ImageNet.
- Utilisation de ResNet18 préentraîné.
- Gel des couches préentraînées et entraînement de la couche finale.
- Optimisation avec Adam et CrossEntropyLoss.
- Conservation des statistiques BatchNorm préentraînées.
- Sélection du meilleur modèle selon l’accuracy de validation.
- Sauvegarde et rechargement du modèle pour prédire de nouvelles images.

## Résultats

Le meilleur modèle a obtenu une accuracy de validation de **96,08 %**,
soit **147 images correctement classées sur 153**.

| Classe | Precision | Recall | F1-score |
|--------|-----------|--------|----------|
| Ants   | 0,957     | 0,957  | 0,957    |
| Bees   | 0,964     | 0,964  | 0,964    |

L’évaluation comprend les courbes de perte, une matrice de confusion
et une inspection visuelle des six erreurs de classification.

## Exécution

1. Installer les dépendances : `pip install -r requirements.txt`.
2. Placer le dataset dans les dossiers indiqués.
3. Ouvrir `image_classification.ipynb`.
4. Exécuter les cellules dans l’ordre.
5. Adapter le chemin de l’image pour tester une photo personnelle.

Les données et les poids du modèle ne sont pas inclus dans le dépôt.
Le notebook permet d’entraîner et de sauvegarder le modèle.

## Limites

Le dataset est petit. Le jeu de validation a également servi
à sélectionner le meilleur modèle : ces résultats ne constituent
donc pas une évaluation sur un jeu de test indépendant.

Le modèle ne reconnaît que deux classes et attribue toujours
une image à l’une d’elles, même si elle représente autre chose.