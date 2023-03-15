# Entretien technique rapide

Voilà quelques questions pour un premier entretien technique rapide (téléphonique ou visio) pour évaluer globalement les connaissances d'un candidat pour être développeur Symfony.

Il va de soit qu'il doit être adapté selon votre contexte ! (Junior/Senior/Lead etc.)

🔴 **= Éliminatoire si ne sait pas**

## PHP

- On peut mettre un try, on peut un catch, que peut-on mettre d'autre comme bloc ?
  - `finally`
- Qu'est-ce qu'une classe abstraite ? 🔴
  - Une classe qui ne peut-être instanciée que par un enfant qui l'hérite.
- Qu'est-ce qu'une classe/méthode finale ?
  - Une classe/méthode qui ne peut pas être héritée
- Qu'est-ce qu'une interface ? 🔴
  - Elle contient une liste de définition de méthode que la classe devra définir si celle-ci implémente cette interface.
- Qu'est-ce qu'un trait ?
  - Il permet d'injecter des méthodes ou des propriétés dans des classes, sans passer par l'héritage classique.
- Qu'est-ce qu'a apporté PHP6 ?
  - Rien, la version 6 n'existe pas
- Dernière version finale de PHP ?
  - 8.2
- Qu'est-ce qu'a apporté PHP8 en terme de code ?
  - Arguments nommés (pour omettre des paramètres optionnels, indépendance de l'ordre des arguments)
  - Attributs natifs (sans utilisation de PhpDoc)
  - Simplication de la définition des propriétés d'une classe au niveau du constructeur
  - les types d'union avec | (int|string)
  - Match expression (simplification typée de switch - pseudo tableau avec clé respectant)
  - Nullsafe operator (pour éviter le chainage de if pour vérifier qu'une méthode d'un objet retourne null)
  - Comparaisons entre les chaînes de caractères et les nombres plus saines
  - Erreurs de type cohérent pour les fonctions internes
- J'ai besoin de savoir si une valeur existe dans un tableau, et sinon, appliquer une valeur par défaut. Attention, j'interdit toute utilisation de isset(), d'opérateur ternaire, sans utiliser de
  méthode
  - <code lang="php">$a['toto'] ?? 2</code> utilisation d'un "opérateur null coalescent" (double point d'interrogation)
- J'ai un fichier de 1Go de données à traiter ligne par ligne en PHP. Quelle est votre façon de procéder pour éviter une utilisation de mémoire monstrueuse ?
  - un fopen de lecture et un fopen en écriture, puis fread et fwrite à chaque ligne
  - utilisation des yield / générateurs

## Commandes systèmes

- Lister le contenu d'un répertoire 🔴
  - `ls`
- Changer de répertoire 🔴
  - `cd`
- Rechercher une occurence dans un fichier
  - `grep`
- Compter le nombre de ligne d'un fichier
  - `wc`

## Symfony

- Version actuelle de Symfony
  - 6.2
- Moteur de template par défaut de Symfony 🔴
  - Twig
- Peut-on utiliser un autre moteur ?
  - Oui
- Qui a créé Symfony ?
  - Fabien Potencier / SensioLabs
- Peut-on utiliser des composants de Symfony sans utiliser le framework de Symfony ?
  - Oui
- Peut-on utiliser des composants non lié à Symfony dans un projet Symfony ?
  - Oui
- Qu'est-ce que composer ? 🔴
  - Composer est un outil de gestion de dépendance en PHP. Il vous permet de déclarer les librairies dont votre projet dépend, et il va vous les gérer (installation/mise à jour). C'est vraiment l’outil de gestion de dépendance en PHP.
- Quels composants utilisez-vous au quotidien ? Pouvez-vous m'en citer 5 ?
  - Voir : https://symfony.com/components
- A quoi sert le serializer ? 🔴
  - Voir : https://api-platform.com/docs/core/serialization/
- Qu'est-ce qu'une décoration de service ?
  - Voir : https://symfony.com/doc/current/service_container/service_decoration.html

## Recherche de bug

- On vous demande de modifier une fonctionnalité ou de corriger un bug sur un outil (application web). Vous ne savez pas où cela se trouve dans le projet. Comment procédez-vous ?
  - recherche d'après la stack trace, si disponible
  - recherche de la route correspondant à l'URL puis du controlleur et je remonte au fur et à mesure dans le code du projet
  - Recherche d'un texte présent sur l'interface
  - etc...

## MySQL

- Quels principaux types de jointure entre les tables en MySQL ? 🔴
  - `INNER JOIN`, `LEFT JOIN` et `RIGHT JOIN`
- Différences entre les 3
- Quel type d'encodage utilisez-vous pour créer des champs texte en MySQL ? Pourquoi ?
  - `UTF8` -> bien !
  - Pas `UTF8` -> Comment je stocke du chinois ou japonais dans ma table ?
- Et si je veux stocker des émoticônes ? Pourquoi l'UTF8 simple ne fonctionnera pas ?
  - L'`UTF8` simple est stocké sur 3 octets, ce qui ne permet pas le stockage des emojis qui en demande 4. (`UTF8MB4`)

## GIT	

- Quelle commande permet de basculer sur une autre branche ? 🔴
  - `git switch` (branche) ou `git checkout` (branche)