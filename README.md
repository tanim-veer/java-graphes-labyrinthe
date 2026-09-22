# 🧩 Graphes et Labyrinthe

Projet étudiant – **BUT1 Informatique** – Groupe 108
Réalisé par : **VEER Tanim**, **NGUELET Ilan**, **BEN KHELIFA Elyes**, **MEBALEY KAHEL Ethan**

---

## 🎯 Objectif

Modéliser des graphes et générer / résoudre des labyrinthes à l'aide de techniques algorithmiques classiques :
- Représentation d'un graphe orienté et valué (liste d'adjacence)
- Recherche de plus court chemin (Dijkstra)
- Adaptation d'un labyrinthe en graphe (patron Adapter)
- Animation visuelle de la résolution, case par case

Projet à la fois pédagogique (structures de données, algorithmie) et applicatif (interface graphique, visualisation).

---

## 🚀 Démo

_Captures à ajouter : lancer `Animation` sur un labyrinthe du dossier `bench/` et faire une capture de la fenêtre pendant et après la résolution._

---

## 🛠️ Technologies

- **Langage :** Java 17+
- **Bibliothèque fournie :** `libs/maze.jar` (représentation et affichage des labyrinthes, fournie dans le cadre du cours)
- **Outils :** IntelliJ IDEA, Git

---

## 📂 Structure du projet

```text
.
├── src/
│   ├── partie1/
│   │   ├── graphe/      # Interfaces et implémentation de graphe (Graph, VarGraph, GrapheHHAdj)
│   │   ├── dijkstra/    # Algorithme de plus court chemin
│   │   └── test/        # Tests de la partie graphe
│   └── partie2/
│       ├── adaptator/   # Adaptateur Labyrinthe -> Graphe (GraphMaze)
│       ├── applications/# Animation (interface graphique) et Checker (vérification)
│       └── test/        # Tests de la partie labyrinthe
├── bench/               # Labyrinthes de test (.maze) et distances attendues (.dist)
├── libs/maze.jar        # Bibliothèque labyrinthe fournie
└── architecture.pdf     # Schéma d'architecture du projet
```

---

## ▶️ Lancement

**Prérequis :** JDK 17 ou version compatible.

### Depuis IntelliJ IDEA

Ouvrir le projet, configurer le SDK, ajouter `libs/maze.jar` aux dépendances du module, puis exécuter la classe `partie2.applications.Animation` (anime la résolution de tous les labyrinthes du dossier `bench/`) ou `partie2.applications.Checker` (vérifie les distances calculées par rapport aux fichiers `.dist`).

### En ligne de commande

```bash
git clone https://github.com/tanim-veer/java-graphes-labyrinthe.git
cd java-graphes-labyrinthe

# Compilation
mkdir out
javac -cp libs/maze.jar -d out $(find src -name "*.java")

# Lancement (Linux/macOS : classpath séparé par ':')
java -cp "out:libs/maze.jar" partie2.applications.Animation

# Windows (classpath séparé par ';')
java -cp "out;libs/maze.jar" partie2.applications.Animation
```

Remplacer `Animation` par `Checker` pour lancer la vérification des distances sans interface graphique.

---

## ✅ Fonctionnalités clés

- Construction d'un graphe orienté et valué à partir d'une chaîne de caractères (`GrapheHHAdj.peupler`)
- Algorithme de Dijkstra générique (fonctionne sur tout type de sommet hachable)
- Adaptation d'un labyrinthe en graphe via le patron **Adapter** (`GraphMaze`)
- Animation de la résolution : coloration de l'entrée/sortie, annotation des distances calculées, tracé du chemin final
- Vérification automatique des distances calculées par rapport à des jeux de test (`bench/`)

---

## 🔍 Points techniques

- `Dijkstra<T>` implémente l'interface `ShortestPath<T>`, découplée de la structure de graphe : elle fonctionne aussi bien sur un graphe classique (`GrapheHHAdj`) que sur un labyrinthe adapté en graphe (`GraphMaze`)
- Détection des poids négatifs (`IllegalArgumentException`), non gérés par Dijkstra
- Le callback `Animator<T>` découple le calcul de son affichage : `Dijkstra` ne dépend d'aucune classe d'interface graphique

---

## 📚 Limites et améliorations possibles

- Ajouter d'autres algorithmes (A*, BFS/DFS animés) pour comparer les performances
- Export du labyrinthe résolu en image
- Tests unitaires plus complets sur `GrapheHHAdj` (arcs dupliqués, graphe vide)

---

## 👥 Équipe

- **Tanim Veer** – [@tanim-veer](https://github.com/tanim-veer)
- **Ilan Nguelet**
- **Elyes Ben Khelifa**
- **Ethan Mebaley Kahel**
