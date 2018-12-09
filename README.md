# Générateur de site statique

Ceci est un projet proposé à des étudiants en Python.

## Qu'est-ce qu'un site statique

Un site internet statique est un site composé uniquement de fichiers présents dans un dossier :

* des fichiers HTML,
* des fichiers CSS,
* des fichiers JavaScript,
* des images,
* des vidéos,
* …

Cela s'oppose aux sites internet dynamiques, où certains de ces fichiers sont générés à la volée par du logiciel, à partir par exemple de données dans une base de données.

## Héberger un site statique

Héberger un site dynamique est plus complexe que pour un site statique, il faut en effet installer le logiciel qui va générer les fichiers à la volée. Par contre, héberger un site statique est relativement simple, il suffit d'avoir un petit serveur web qui met à disposition le dossier contenant les fichiers statiques.

### Github

Github fournit un hébergement gratuit de site statique. Il suffit de créer un dépôt git avec Github, et de committer dans une branche spécifique. Votre site est alors accessible à l'adresse suivante : https://votre_login.github.io/votre_nom_de_depot/

Plus de renseignement sur :

* https://pages.github.com/
* https://www.christopheducamp.com/2013/12/21/demarrer-avec-pages-github/
* https://developer.mozilla.org/fr/docs/Apprendre/Utiliser_les_pages_GitHub
  
### Utiliser un serveur web

Des outils commes Apache ou Nginx permettent de rendre accessible votre site par internet ou intranet :
* https://httpd.apache.org/docs/trunk/fr/getting-started.html
* http://sametmax.com/servir-des-fichiers-statiques-avec-nginx/
* https://doc.ubuntu-fr.org/nginx
* https://nginxconfig.io/

Python vous fournit un serveur web minimaliste, par exemple pour aller sur http://localhost:8080/ et y voir le site statique dont les fichiers sont dans `./dossier_de_mon_site/`.

```
python -m http.server 8080  --directory ./dossier_de_mon_site/
```

## Génerer un site statique

Les fichiers compris par un navigateur internet sont aux formats HTML/CSS/JavaScript. Vous n'avez peut-être pas envie de taper du HTML quand vous écrivez un blog. Il serait pratique de générer les pages web à partir d'un format textuel simple, comme le markdown (https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf), langage utilisé pour écrire le document que vous lisez actuellement (https://raw.githubusercontent.com/vpoulailleau/site_statique/master/README.md).

Certains outils open-source le font déjà, dont certains connus et en Python :

* https://blog.getpelican.com/
* https://www.getlektor.com/
* https://www.mkdocs.org/
* https://github.com/eudicots/Cactus
* http://www.sphinx-doc.org/en/master/
* https://www.getnikola.com/

## Projet

Vous allez réaliser un outil convertissant un dossier de fichiers markdown et d'images en un autre dossier contenant les fichiers d'un site statique. Du HTML sera généré à partir du markdown, et cet HTML sera mélangé avec des modèles de pages web pour générer des pages toutes conformes au même modèle (par exemple avec le même logo, le même sommaire de site internet, le même fichier CSS référencé…).

Les fichiers markdown peuvent être créés :

* avec Visual Studio Code
* avec https://github.com/ncornette/Python-Markdown-Editor
* avec https://pandao.github.io/editor.md/en.html
* avec https://dillinger.io/
* …

### Réalisation d'une interface en ligne de commande

Vous allez réaliser un outil en ligne de commande pour générer les fichiers du site statique. Il prendra au moins comme paramètres :

* -i ./un_dossier ou --input-directory ./un_dossier : le chemin du dossier de fichiers source (contenant les fichiers markdown)
* -o ./un_autre_dossier ou --output-directory ./un_autre_dossier : le chemin du dossier où seront mis les fichiers générés pour le site statique
* -t ./autre_dossier ou --template-directory ./autre_dossier : éventuellement le dossier contenant des modèles de pages web à compléter
* -h ou --help : pour afficher de l'aide pour exliquer les paramètres de la commande

Vous pouvez utiliser :

* sys.argv (mais je ne vous le conseille pas, https://docs.python.org/fr/3/library/sys.html#sys.argv)
* argparse (https://docs.python.org/fr/3/howto/argparse.html)
* click (https://click.palletsprojects.com/en/7.x/)

### Conversion de markdown vers HTML

Vous devez au moins convertir les syntaxes suivantes :

* `#`, un titre de niveau 1 en `<h1>`
* `##`, un titre de niveau 2 en `<h2>`
* `###`, un titre de niveau 3 en `<h3>`
* Convertir les listes non ordonées en `<ul>` et `<li>`
* Convertir les URL (http://quelquechose.com) en `<a href="http://quelquechose.com">http://quelquechose.com</a>`
* `*un texte*`, un texte important en `<em>un texte</em>`

Vous pouvez faire ces conversions en utilisant au choix :

* les fonctions de base de Python pour les chaînes de caractères
* les expressions régulières (https://docs.python.org/fr/3/library/re.html)
* un package de la communauté
  * https://github.com/Python-Markdown/markdown
  * https://github.com/trentm/python-markdown2

### Qualité du code

Vous veillerez à respecter :

* la PEP 8 :  https://www.python.org/dev/peps/pep-0008/
* la PEP 20 : https://www.python.org/dev/peps/pep-0020/
* plus de détails sur https://vpoulailleau.wordpress.com/2018/12/04/un-code-pythonique/

### Rendu sur Github

Votre projet Python sera posté sur Github et un lien sera fourni.

### Projet open-source

Vous pouvez faire un projet libre et open-source. Beaucoup de projets Python utilisent la license MIT ou BSD 3 clauses, ces licences sont faciles à lire et très permissives. Vous pouvez aussi utiliser une licence plus stricte comme la GPL qui imposent que les versions modifiées de votre projet soient aussi open-source.

Vous pouvez lire la licence BSD 3 clauses du projet https://github.com/vpoulailleau/simplelogging à l'adresse suivante https://github.com/vpoulailleau/simplelogging/blob/master/LICENSE.

Vous pouvez faire en sorte que votre projet soit installable par la communauté Python en le diffusant sur le Python Package Index (https://pypi.org/), comme par exemple https://pypi.org/project/simplelogging/.

Pour vous aidez dans cette aventure, vous pouvez utiliser https://github.com/audreyr/cookiecutter-pypackage.

### Objectifs

Il va de soi que se documenter, copier du code (dans le respect des licences), discuter avec d'autres codeurs est vivement recommandé pour progresser. Regardez comment font les autres, et faites à votre façon. Soyez capables d'expliquer ce que vous avez fait.

Pour rappel toutefois, un code sans licence est par défaut protégé par le droit d'auteur, vous n'avez donc pas le droit de le copier.

Bon apprentissage, et bon projet.