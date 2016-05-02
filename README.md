# TP Opower

Le tp sur Opower comprenant la partie `JPA` ainsi que la partie `AngularJS` a été réalisé en utilisant [`jhipster`](https://jhipster.github.io).

## Création des entités
Afin de créer les entités `Person`, `House`, `Device` et `Heater` nous avons utilisé `JDL Studio` qui va générer un fichier `.jh`. Ensuite il a suffit d'appliquer la commande suivante dans le terminal : 
```sh
yo jhipster:import-jdl generatedFile.jh
```
Notre fichier JDL avec les entités, les relations et le diagramme UML est disponible à cette adresse : [http://jhipster.github.io/jdl-studio/](http://jhipster.github.io/jdl-studio/#view/entity%20Person%20%7B%0A%20%20%20%20name%20String%2C%0A%20%20%20%20email%20String%0A%7D%0A%0Aentity%20House%20%7B%0A%09name%20String%2C%0A%20%20%20%20size%20Integer%2C%0A%20%20%20%20nbRoom%20Integer%0A%7D%0A%0Aentity%20Device%20%7B%0A%09name%20String%2C%0A%20%20%20%20conso%20Integer%0A%7D%0A%0Aentity%20Heater%20%7B%0A%09name%20String%2C%0A%20%20%20%20conso%20Integer%0A%7D%0A%0Arelationship%20ManyToMany%20%7B%0A%09Person%7Bfriend%7D%20to%20Person%7BfriendOf%7D%0A%7D%0A%0Arelationship%20OneToMany%20%7B%0A%20%20%20%20House%7Binhabitant%7D%20to%20Person%7Bhouse%7D%0A%7D%0A%0Arelationship%20OneToMany%20%7B%0A%09House%7Bdevice%7D%20to%20Device%7Bhouse%7D%0A%7D%0A%0Arelationship%20OneToMany%20%7B%0A%09House%7Bheater%7D%20to%20Heater%7Bhouse%7D%0A%7D)

## Configuration de la base de données
Avant de builder le projet, il est nécessaire de bien configurer la base de données pour le projet.

Dans un premier temps il faut créer une base de données MySQL avec un nom au choix (par exemple `opower`).

Ensuite il faut configurer la connexion à cette base dans le fichier `src/main/resources/config/application-dev.yml` en y modifiant ces lignes : 
```yaml
    datasource:
        driver-class-name: com.mysql.jdbc.jdbc2.optional.MysqlDataSource
        url: jdbc:mysql://localhost:3306/opower # nom de la base créée
        name: opower # nom de la base créée
        username: root # nom utilisateur mysql
        password: root # password utilisateur mysql
```

## Builder le projet

A la racine du projet effectuer ces commandes :

Installation des dépendances du package.json (outils pour le développement : `Bower`, ...) : 
```sh
npm install
```
Installation de l'outil de commande de `Grunt` : 
```sh
npm install -g grunt-cli
```
Installation des dépendances du bower.json (librairies CSS/JS : `bootstrap`, `angular`, ...) : 
```sh
bower install
```
Lancer le projet. L'application sera ensuite disponible à l'adresse `http://127.0.0.1:8080` : 
```sh
mvn
```
Pour lancer le serveur grunt en parallèle du serveur créé par la commande `mvn`, il suffit de lancer la commande `grunt` dans un nouvel onglet du terminal.

<br>
###### Clément Goachet - Paul Chemin

<br>
# README généré par jhipster

This application was generated using JHipster, you can find documentation and help at [https://jhipster.github.io](https://jhipster.github.io).

Before you can build this project, you must install and configure the following dependencies on your machine:

1. [Node.js][]: We use Node to run a development web server and build the project.
   Depending on your system, you can install Node either from source or as a pre-packaged bundle.

After installing Node, you should be able to run the following command to install development tools (like
[Bower][] and [BrowserSync][]). You will only need to run this command when dependencies change in package.json.

    npm install

We use [Grunt][] as our build system. Install the grunt command-line tool globally with:

    npm install -g grunt-cli

Run the following commands in two separate terminals to create a blissful development experience where your browser
auto-refreshes when files change on your hard drive.

    mvn
    grunt

Bower is used to manage CSS and JavaScript dependencies used in this application. You can upgrade dependencies by
specifying a newer version in `bower.json`. You can also run `bower update` and `bower install` to manage dependencies.
Add the `-h` flag on any command to see how you can use it. For example, `bower update -h`.

# Building for production

To optimize the opower client for production, run:

    mvn -Pprod clean package

This will concatenate and minify CSS and JavaScript files. It will also modify `index.html` so it references
these new files.

To ensure everything worked, run:

    java -jar target/*.war --spring.profiles.active=prod

Then navigate to [http://localhost:8080](http://localhost:8080) in your browser.

# Testing

Unit tests are run by [Karma][] and written with [Jasmine][]. They're located in `src/test/javascript` and can be run with:

    grunt test



# Continuous Integration

To setup this project in Jenkins, use the following configuration:

* Project name: `opower`
* Source Code Management
    * Git Repository: `git@github.com:xxxx/opower.git`
    * Branches to build: `*/master`
    * Additional Behaviours: `Wipe out repository & force clone`
* Build Triggers
    * Poll SCM / Schedule: `H/5 * * * *`
* Build
    * Invoke Maven / Tasks: `-Pprod clean package`
* Post-build Actions
    * Publish JUnit test result report / Test Report XMLs: `build/test-results/*.xml`

[JHipster]: https://jhipster.github.io/
[Node.js]: https://nodejs.org/
[Bower]: http://bower.io/
[Grunt]: http://gruntjs.com/
[BrowserSync]: http://www.browsersync.io/
[Karma]: http://karma-runner.github.io/
[Jasmine]: http://jasmine.github.io/2.0/introduction.html
[Protractor]: https://angular.github.io/protractor/
