
# 🌊 Tableau de Bord - Surveillance des Ressources en Eau au Maroc

## 📋 Description du Projet
Ce projet implémente un système complet de surveillance et de prédiction des ressources en eau au Maroc, comprenant :

- **Modèle de Machine Learning** : Prédiction des périodes de sécheresse avec un score R² de `0.996`
- **Tableau de bord interactif** : Interface web moderne avec graphiques et analyses en temps réel
- **API REST** : Endpoints pour accéder aux données et aux prédictions

---

## 🚀 Installation et Configuration

### Prérequis
- Python 3.8 ou supérieur
- `pip` (gestionnaire de paquets Python)

### Étapes d'installation

1. **Extraire l'archive du projet**
   ```bash
   tar -xzf water_dashboard_project.tar.gz
   cd water_dashboard
````

2. **Créer un environnement virtuel**

   ```bash
   python -m venv venv
   ```

3. **Activer l'environnement virtuel**

   * **Windows** :

     ```bash
     venv\Scripts\activate
     ```
   * **macOS/Linux** :

     ```bash
     source venv/bin/activate
     ```

4. **Installer les dépendances**

   ```bash
   pip install -r requirements.txt
   ```

5. **Copier les fichiers de données et modèle**
   Assurez-vous que ces fichiers sont dans le répertoire racine du projet :

   * `consolidated_data_cleaned.xlsx`
   * `drought_prediction_model.pkl`
   * `model_evaluation_metrics.txt`

---

## 🏃‍♂️ Lancement de l'application

1. **Démarrer le serveur Flask**

   ```bash
   python src/main.py
   ```

2. **Accéder au tableau de bord**
   Ouvrez votre navigateur et allez à : [http://localhost:5000](http://localhost:5000)

---

## 📊 Fonctionnalités du Tableau de Bord

### Statistiques Générales

* Nombre de régions surveillées : **36**
* Sécheresse moyenne : **22.5%**
* Sécheresse maximale : **60.0%**
* Total d'enregistrements : **2,592**

### Graphiques Interactifs

1. Évolution du Pourcentage de Sécheresse (graphique linéaire par région)
2. Températures par Région (barres)
3. Précipitations par Région (barres)
4. Niveaux des Barrages (secteurs)

### Analyse par Région

* Sélection d'une région spécifique
* Analyse détaillée du pourcentage moyen de sécheresse
* Classification du risque (**Faible / Modéré / Élevé**)

---

## 🔧 Structure du Projet

```
water_dashboard/
├── src/
│   ├── main.py                 # Point d'entrée Flask
│   ├── routes/
│   │   ├── user.py              # Routes utilisateur
│   │   └── dashboard.py         # Routes tableau de bord
│   ├── models/
│   │   └── user.py              # Modèles DB
│   ├── static/
│   │   └── index.html           # Interface dashboard
│   └── database/
│       └── app.db               # SQLite DB
├── venv/                        # Environnement virtuel
├── requirements.txt             # Dépendances
└── README_INSTALLATION.md       # Ce fichier
```

---

## 🌐 API Endpoints

### Données

* `GET /api/dashboard/data` : Toutes les données
* `GET /api/dashboard/statistics` : Statistiques générales
* `GET /api/dashboard/region/<nom_region>` : Données d'une région

### Prédiction

* `POST /api/dashboard/predict` : Prédire le pourcentage de sécheresse

---

## 🧠 Modèle de Machine Learning

### Caractéristiques

* Algorithme : **Random Forest Regressor**
* Score R² : **0.996** (excellent)
* RMSE : **1.65**
* Variables d'entrée : 25 (température, précipitations, humidité, etc.)

**Utilisation :**
Le modèle est chargé automatiquement par l'API et accessible via `/api/dashboard/predict`.

---

## 🔍 Données Utilisées

* Données météorologiques : température, précipitations, humidité
* Niveaux des barrages et nappes phréatiques
* Indices de sécheresse (SPI)
* Données géographiques : latitude, longitude
* Évapotranspiration (ET0)

---

## 🛠️ Dépannage

### 1. Erreur "Module not found"

* Vérifier que l'environnement virtuel est activé
* Réinstaller les dépendances :

  ```bash
  pip install -r requirements.txt
  ```

### 2. Erreur base de données

* SQLite est créé automatiquement au premier lancement

### 3. Fichiers manquants

* Vérifier présence de :

  * `consolidated_data_cleaned.xlsx`
  * `drought_prediction_model.pkl`

### 4. Port 5000 occupé

* Modifier dans `src/main.py` :

  ```python
  app.run(host='0.0.0.0', port=5001, debug=True)
  ```

---

## 📈 Améliorations Possibles

* Ajout de nouvelles sources de données
* Alertes automatiques
* Cartes interactives
* Notifications email
* Export des données (API)

---

## 📞 Support

En cas de problème :

1. Vérifier tous les fichiers
2. Activer l'environnement virtuel
3. Installer les dépendances
4. Libérer le port 5000

---
