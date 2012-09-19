# Plaisir Maths: dépôt GIT du site web

## Installation

### Clôner ce dépôt

```bash
git clone git@github.com:plaisir-maths/www.git
cd www
git remote rename origin github
```

### Installer les gemmes

```bash
bundle install
```

### Installer la base de données

```bash
rake db:create
rake db:migrate
rake db:seed
```

## Lancement

```bash
rails server
```

## Se lier aux serveurs

### Installer la toolbelt Heroku (si jamais fait) et se connecter

```bash
wget -qO- https://toolbelt.heroku.com/install.sh | sh
heroku login
```

### Connecter les serveurs au GIT local (en tant que remotes "stage" et "production")

```bash
git remote add stage git@heroku.yann:plaisir-maths-www-stage.git
git remote add production git@heroku.yann:plaisir-maths-www.git
```

## Uploader des modifications

### Agréger les modifications dans des "paquets" de modifications

```bash
git commit -am "un descriptif de mes changements"
```

### Envoyer les paquets de modifications sur le Github (ici)

```bash
git push github master
```

### Envoyer les paquets de modifications sur le serveur "de stage"

```bash
git push stage master
```

### Envoyer les paquets de modifications sur le serveur "de production"

```bash
git push production master
```

## Récupérer les modifications des autres développeurs

Il faut d'abord mettre en paquet les modifications locales:

```bash
git commit -am "encapsulation temporaire pour pull"
```

puis récupérer les modifications:

```bash
git pull github master
```

## Agir sur un des serveurs

### La commande générique

Tout commande locale `xx yyy zz` peut exécutée sur le serveur SSS avec `heroku run xx yyy zz --app SSS`.
cf les exemples suivants.

### Initialiser la base de données du serveur "de stage"

```bash
heroku run rake db:migrate --app plaisir-maths-www-stage
heroku run rake db:seed --app plaisir-maths-www-stage
```

### Initialiser la base de données du serveur "de production" (à ne jamais faire, a priori)

```bash
heroku run rake db:migrate --app plaisir-maths-www
heroku run rake db:seed --app plaisir-maths-www
```

### Redémarrer les serveurs

```bash
heroku restart --app plaisir-maths-www-stage
heroku restart --app plaisir-maths-www
```
