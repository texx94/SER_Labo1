# Sérialisation - Labo 1

## Modélisation XML et DTD

### Introduction

Pour notre premier laboratoire de sérialisation, il nous a été demandé de créer une DTD qui permet de représenter des tournois d'échec. Ces tournois doivent inclure des joueurs, des résultats et un historique des coups pour chaque parties jouée.

Comme nous n'avons aucune expérience en XML/DTD avant ce cours, nous nous sommes particulièrement appuyé sur le cours afin d'atteindre le but fixé.

### DTD

Dans un premier temps, nous avons choisi de commencer par écrire la DTD. Nous avons fais ce chois car, selon nous, il est plus simple d'écrire les règles dans un premier temps puis de les suivre lors de l'écriture d'un XML.

Pour commencer, nous avons défini que la racine de la DTD serai la fédération suisse d'échec et que celle-ci serait composée de tournois et de joueurs. Nous avons décidé de mettre les joueurs directement dans la première balise et non pas dans chaque tournoi afin d'offrir la possibilité d'avoir des joueurs qui jouent dans plusieurs tournois (ce qui est le cas dans la réalité).

Ensuite, nous avons décidé qu'un tournoi regroupe des parties qui sont elles-mêmes composées d'un arbitre, d'une date, d'une heure, d'un score, des deux camps et d'une liste de coups joués. De plus, nous utilisons deux **IDREF** pour assigner les joueurs à leur camp respectif; un dans la balise **EMPTY** blanc et un dans la balise **EMPTY** noir.

Concernant les joueurs, nous les représentons avec un nom, un prénom et son niveau ELO.

Pour finir, nous avons modélisé la liste de coups de cette manière. Les coups peuvent être un déplacement, une élimination, une promotion, un échec ou un roque. Dans le cas d'un déplacement, nous prenons la pièce concernée, son point d'arrivée et sont point de départ (fac.). Les trois types de coups suivant sont une composition d'un déplacement et d'une information supplémentaire comme montré ci-dessous : 

+ Elimination => déplacement + pièce éliminée
+ Promotion => déplacement + pièce remplacée
+ Echec => déplacement + type d'échec

Puis pour le roque, nous ne gardons que le nom du roque (Grand Roque ou Petit Roque). Nous avons décidé cela car le roque implique de toute façon le roi et une tour et fini toujours de la même manière. Il est donc inutile de garder les deux déplacement impliqué dans cette manœuvre.

### Exemple d'utilisation

Pour notre exemple d'utilisation, nous avons écrit un XML qui représente la situation suivante.

+ La racine contient deux tournois (Junior et Master) et quatre joueurs.
+ Chaque tournoi est composé de deux parties (allé-retour) entre les deux joueurs du tournoi.
+ Les parties sont toute semblable et représente une victoire des blancs en 3 coups. Voir https://fr.wikihow.com/faire-%C3%A9chec-et-mat-en-trois-coups.
+ La deuxième partie du deuxième tournoi ajoute une promotion et un roque en guise de test.

### Validation

![validation](C:\Users\lgill\OneDrive\Documents\HEIG-VD\SER\Labo\Labo 1\validation.png)

### Réponses aux questions

#### Imaginons que vous souhaitez enregistrer le classement ELO que chaque joueur d’une partie avait au moment où elle a été jouée, qu’est-ce qu’il faudrait modifier dans votre DTD ?

Il faudrait modifier la balise **blanc/noir** de **partie** afin d'y ajouter un **#PCDATA** représentant le classement ELO du participant blanc ou noir.

#### Est-ce possible dans votre DTD de représenter le fait qu’il ne peut y avoir que 20 parties au maximum dans un tournoi ? Si oui, comment ?

Non il n'est pas possible de le faire.

#### Est-ce possible dans votre DTD de représenter le fait que les 2 joueurs d’une partie doivent être différents ? Si oui, comment ?

Dans notre implémentation de DTD, nous ne faisons pas de contrôle sur les joueurs. il est donc possible de jouer contre soi-même.

### Conclusion

Pour conclure, nous pensons avoir atteint les objectifs et que notre solution est acceptable. Au vue de nos connaissances avant la réalisation de ce laboratoire, nous sommes satisfait du résultats.

En outre, nous trouvons dommage que nous soyons que très peu formé à la réalisation de cette DTD et d'un XML correspondant et que la principale difficulté est de fouiller internet.

Nous sommes toutes fois content d'y être parvenu et nous pensons avoir améliorer nos compétences.