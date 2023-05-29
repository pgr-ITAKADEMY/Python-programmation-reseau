# Python programmation réseau

## Cours - Intro Python
### 1. Hello world
`print()` Permet d'afficher du texte. Ainsi le traditionnel hello_world.py
```python3
# ./hello_world.py
print("Hello World")
```

Executer le programme avec:
```bash
$ python hello_world.py
```

### 2. Le header Python
Deux versions de python cohabitent. La version 2 et la version 3. La version 2 est dépréciée et ne doit plus être utilisée. Néanmoins des programmes "historiques" n'ont pas encore fait la migration vers python3. Ainsi sur certains systèmes les 2 versions de Python peuvent être installés. Afin de guider l'interpr"teur sur la version a utiliser l'header peut être rajouté en entête du fichier python:
```python
#!/usr/bin/env python3
```

### 3. Les types de bases
En python les variables n'ont pas de type et peuvent en changer de façon implicite.
- Les int et float représentent les nombres. `int` pour les entiers, `float` pour les nombres a virgules.
```python3
ma_variable_int = 1
ma_variable_float = 1.3
print(ma_variable_int + 1)  # => 2
print(ma_variable_float + 1.5)  # => 2.8
# - pour la soustraction
# / pour la division
# * pour la multiplication
# % pour le modulo (reste de la division euclidenne)

# Auto increment
ma_variable_int += 1
print(ma_variable_int)  # => 2
# -= pour décrement
# *= pour multiplication
# /= pour division
```

- Les booléens
```python3
variable_Vrai = True  # Majuscule obligatoire
variable_Faux = False  # Majuscule obligatoire
variable_Vrai2 = not False  # inversion avec le keyword 'not'
```

- Les strings
Les strings peuvent être définies de trois façons:
```python3
ma_variable_string = "Bonjour"  # une string avec "
ma_var2_string = 'Nouvelle string'  # une string avec '
ma_var3_string = """C'est une citation "..." E. """  # une string avec """
concatenation = ma_variable_string + ma_var2_string + ma_var3_string # l'operation + sur les string permet la concaténation
print(concatenation)  # => BonjourNouvelle stringC'est une citation "..." E.
```
Les `f-string` sont utilisées car elle permet d'insérer facilement les variables dans la chaîne de caractères à afficher. Elle est précédée d'un `f`, et contenant des expressions entre accolades `{}` qui seront évaluées lors de l'exécution du programme.
```python3
nom = "GRESSIER"
age = 30
print(f"Bonjour {nom}, vous avez {age} ans")  # => Bonjour GRESSIER, vous avez 30 ans
```

- Les listes
Les listes ne sont pas limitées à un unique type de données.
```python3
ma_liste = [1, 2, 3, "quatre"]
ma_liste.append(5)  # ajouter un élément à la fin de la liste
print(ma_liste)
ma_liste.insert(2, "12")  # ajouter "12" a la position 2 de la liste
print(ma_liste)
ma_liste.pop(3)  # retirer l'element a la position 3 de la liste
liste_length = len(ma_liste)  # calculer la longueur d'une liste
print(liste_length)
print(ma_liste.index(2))  # renvoyer la première occurrence de l'élément spécifié dans la liste
print(ma_liste.count(1))  # renvoyer le nombre d'occurrences de l'élément spécifié dans la liste
ma_liste.reverse()  # inverser l'ordre des éléments de la liste
print(ma_liste)
```
Les éléments sont numérotés à partir de 0. Pour accéder au dernier élément de la liste il est possible d'utiliser l'indice -1, l'avant dernier avec l'indice -2 etc.
```python3
ma_liste = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(ma_liste[0])  # => 1
print(ma_liste[3])  # => 4
print(ma_liste[-1])  # => 9
print(ma_liste[-3])  # => 7
ma_liste[1] = "deux"
print(ma_liste)  # => [1, 'deux', 3, 4, 5, 6, 7, 8, 9]
```

Une string étant une liste de caractères il est possible d'accéder à une lettre ou calculer sa longueur comme vu précédemment.
```python3
var = "Bonjour"
print(var[1])  # => o
print(len(var))  # => 7
```

- Les tuples
Un tuple est une liste non modifiable.
```python3
mon_tuple = (1, 2, 3, 4, 5, 6)
print(mon_tuple[2])  # => 3
mon_tuple[1] = 99  # => ERROR!
```

- Les dictionnaires
Un dictionnaire est une structure de données qui enregistre des données dans des paires clés-valeurs, comme dans une structure JSON.
```python3
mon_dict = {
    "nom": "GRESSIER",
    "prenom": "Paul",
    "age": 30
}
```
La clé "nom" référence la valeur "GRESSIER". 
Chaque dictionnaire doit être composé de clés uniques.
```python3
mon_dict = {
    "nom": "GRESSIER",
    "prenom": "Paul",
    "age": 30
}
print(mon_dict["age"])  # => 30, acceder à la valeur
mon_dict["prenom"] = "John"  # modifier la valeur
print(mon_dict)  # => {'nom': 'GRESSIER', 'prenom': 'John', 'age': 30}
mon_dict["adresse"] = "Lune"  # ajouter une nouvelle paire clef-valeur
print(mon_dict)  # => {'nom': 'GRESSIER', 'prenom': 'John', 'age': 30, 'adresse': 'Lune'}
del mon_dict["age"]  # supprimer une paire clef-valeur
print(mon_dict)  # => {'nom': 'GRESSIER', 'prenom': 'John', 'adresse': 'Lune'}
```

### 4. Control flow
- Opérateurs logiques
Dans les conditions, les mots clefs `and` et `or` permettent de cumuler les conditions. La priorité peut être explicité via des parenthèses. `not` permet de renverser un booléen comme dit précédemment.
```python3
print(3 > 1)  # => True, comparaison strict
print(3 >= 1)  # => True, comparaison
print(3 < 1)  # => False, comparaison strict
print(3 <= 1)  # => False, comparaison
print(1 == 1)  # => True
print(1 != 1)  # => False
print(not True)  # => False
print(1 > 2 or 1 < 3)  # => True
print(3 == 3 and 1 == 2)  # => False
```
 
- `if`
En python un block est déterminé par les `:` de l'instruction créant le block et l'indentation du texte au sein du block (par convention, 4 espaces). Les instructions `elif` et `else` sont facultatives. `elif` peut être utilisé autant de fois que souhaité.
```python3
variable = 3
if variable <= 2 and variable >= 0:
    print("ok")
elif variable <= 4:
    print("<=4")  # => <=4
else:
    print("ko")
```

- `match`
Le match est une fonctionnalité pour faciliter la comparaison de valeurs à l'aide de motifs. Cela est souvent appelé switch dans d'autres langages. Le 'cas' `_` est à valeur par défaut comprenant les 'cas' n'ayant pas 'matchés'.
```python3
variable = "chat"
match variable:
    case "chien":
        print("ouaf")
    case "poisson":
        print("bubl")
    case "chat":
        print("miaou")  # => miaou
    case _:
        print("???")
```

- `for`
La boucle `for` est le type de boucle le plus utilisé au sein de Python. Une boucle `for` est utilisée pour itérer sur une string, une liste, un tuple ou un dictionnaire.

```python3
villes = ["lyon", "toulouse", "bordeaux", "paris", "nantes"]
print(villes)
for ville in villes:
    print(ville)

dictionnaire = {
    "clef1": 1,
    "clef2": 2
}

print(list(dictionnaire.items()))  # visualisation de .items()
for key, value in dictionnaire.items():  # itération sur les clefs et valeurs du dict
    print(key)
    print(value)
```

- `while`
La boucle `while` s’exécute jusqu’à ce que la condition soit remplie.
```python3
age = -1
while age < 0:
    age = int(input("Age: "))
```

- `break` et  `continue`
Au sein des boucles (`for` et `while`) il est possible de modifier la séquence d'itération. L'instruction `break` permet de sortir d'une boucle. L'instruction `continue` permet de passer à la prochaine itération de la boucle, sans exécuter le reste du code.
```python3
villes = ["lyon", "toulouse", "bordeaux", "paris", "nantes"]
print(villes)
print("Continue:")
for ville in villes:
    if ville == "paris":
        continue
    print(ville)

print("Break:")
for ville in villes:
    print(ville)
    if ville == "paris":
        break
```

### 5. Saisie utilisateur
```python3
age = input("Quel est votre age ?")  # input renvoie toujours une string
print(type(age))  # => str
print(age)
```
```python3
from getpass import getpass
secret_password = getpass("Votre mot de passe: ")  # getpass n'affiche pas le texte saisie par l'utilisateur
print(type(secret_password))  # => str
```

### 6. Fonctions
Comme dans les autres langages, une fonction est un bloc de code réutilisables qui permettent d'organiser et de structurer le code.
```python3
def fonction_sans_parametre():  # définition
    print("Bonjour, je n'ai pas de paramtre")

fonction_sans_parametre()  # incovation de la fonction
```

Une fonction peut définir des paramètres. Comme partout dans python, ces paramètres ne sont pas typés.
```python3
def salutation(nom):
    print(f"Bonjour {nom} !")

salutation("Paul")
```

 L'appel aux paramètres peut etre explicite. A ce moment l'ordre peut etre modifié. L'appel explicite peut être combiné avec l'appel implicite. A ce moment, les paramètres implicites doivent respecter l'ordre définis.
 ```python3
 def salutation(age, nom, prenom = "Paul"):
     print(f"Bonjour {nom} {prenom} : vous avez {age} ans")
 
salutation(30, prenom = "John", nom = "W.")  # => Bonjour W. John : vous avez 30 ans
 ```

Une fonction peut renvoyer une ou des valeurs (via mécanisme sous jacent de tuple).
```python3
def somme(int1, int2):
    return int1 + int2

print(somme(1, 4))  # => 5

def multi_return(int1, int2):
    res = int1 + int2
    positif = False
    if res > 0:
        positif = True
    
    return res, positif

calc, p = multi_return(1, -5)
print(f"Résultat de 1 + -5 est {calc} et est postif: {p}")  # => Résultat de 1 + -5 est -4 et est postif: False
```

Une fonction peut avoir des valeurs par défaut pour les arguments. Les paramètres avec un argument par défaut doivent être à la fin de la déclaration:
```python3
def maSuperFonction(prenom, nom = "Gressier"):
    print(f"Bonjour {nom} {prenom}")

maSuperFonction("Paul")  # => Bonjour Gressier Paul
maSuperFonction("John", "W.")  # => Bonjour W. John
```

### 7. Package et import
Il est possible d'importer des variables, des fonctions ou des classes définies dans d'autres fichier python. La recherche pour les noms de package se fait par rapport a des dossiers préconfigurés dans une variable d'environnement (hors programme du cours) et dans le répertoire actuel d'exécution du programme python.
Un import peut être effectué depuis un fichier au même niveau.
```python3
# ./file_package.py
def bonjour():
    print("Bonjour depuis file_package.py")
```
Un import peut etre effectué avec un `from x import y` permettant d'importer y dans le namespace actuel.
```python3
# ./main.py
from file_package import bonjour

bonjour()
```
ou bien uniquement avec `import x` qui importe le package sans modifier le namespace.
```python3
import file_package

file_package.bonjour()
```

Un import peut être effectué à travers des dossiers afin d'organiser  plus simplement son code.
```python3
# ./animal_package/cat.py
def meow():
    print("Miaou !")
```
```python3
# ./main.py
from animal_package.cat import meow

meow()
```
ou bien
```python3
" ./main.py
from animal_package import cat

cat.meow()
```

Comme seul le répertoire actuel est ajouté au chemin de recherche des packages, il faut utiliser le chemin absolu partout, y compris au sein du package.
```python3
# ./animals/base.py
def sound(sound):
    return f"The animal do {sound}"
```
```python3
# ./animals/dog.py
from animals.base import sound

def bark():
    print(sound("ouaf !"))
```
```python3
# ./main.py
from animals.dog import bark

bark()
```

Le fichier `__init__.py` est appelé implicitement sur le nom d'un package répertoire.
```python3
# ./animals/__init__.py
CONSTANT_ANIMALS = ("cat", "dog")
```
```python3
# ./main.py
import animals

print(animals.CONSTANT_ANIMALS)
```

### 8. Classes
Une classe est le plan (les règles de comportement) de construction d'un objet. Une instance est l'instanciation de l'objet en utilisant la classe (le plan).
Une classe peut avoir des méthodes. Une méthode est une fonction attachée à un objet. Elle prend systématiquement l'objet `self` en paramètre. `self` réfère a l'instance de objet actuel.
```python3
class Chat:  # définition de la classe
    def miauler(self):
        print("miaou")

felix = Chat()  # instanciation de l'objet
felix.miauler()  # appel de la méthode
```

Il est possible d'associé des variables d'instance via un constructeur ou des getters et setters (abordés plus loin). Une variable d'instance est propre a chaque instance créée. Accéder un une variable d'instance se fait via [instance].[nom_variable]. Ainsi dans une méthode, [instance] vaut `self`
En python le constructeur est unique. La surcharge n'existe pas au sens java.
```python3
class Chat:
    def __init__(self, nom = "Felix"):
        self.nom = nom  # variable d'instance
    
    def miauler(self):
        print(f"{self.nom} fait miaou !")  # accès a la variable d'instance dans la méthode via self

felix = Chat()
tom = Chat("Tom")
felix.miauler()  # => Felix fait miaou !
tom.miauler()  # => Tom fait miaou !
print(felix.nom)  # => Felix, accès a la variable d'instance hors d'une méthode d'objet
```

Il est possible de modifier les variables d'instance des façon suivante:
```python3
class Chat:
    def __init__(self, nom):
        self.nom = nom

    def set_nom(self, nom):  # setter non 'pythonic'
        self.nom = nom

chat = Chat("Felix")
print(chat.nom)  # => Felix
chat.set_nom("Tom")  # modification via une méthode
print(chat.nom)  # => Tom
chat.nom = "Minet"  # modification hors méthode
print(chat.nom)  # => Minet
```

Il est possible de déclarer des variables de classe. Ces variables sont propres à la classe, et partagées entre toutes les instances. De plus, il est possible de déclarer des méthodes de classe permettant de manipuler la classe. Cela utilise l'annotation `@classmethod` et le paramètre `cls` est systématiquement passé en premier argument (à la place de `self`).
```python3
class Chien:
    maitre = "John"  # variable de classe
    
    def aboyer(self):
        print(f"Le chien de {self.maitre} aboie !")
        
    @classmethod
    def changer_maitre(cls, nv_maitre):
        cls.maitre = nv_maitre

rex = Chien()
snoopy = Chien()
rex.aboyer()  # => Le chien de John aboie !
snoopy.aboyer()  # => Le chien de John aboie !
rex.changer_maitre("Paul")  # comme maitre est une variable de classe, le maitre change pour tout les chiens, car la variable est partagée
rex.aboyer()  # => Le chien de Paul aboie !
snoopy.aboyer()  # => Le chien de Paul aboie !
```

Finalement, il est possible de déclarer des méthodes statiques via l'annotation `@staticmethod`. Les méthodes statiques n'ont aucun lien avec l'instance ou la classe.
```python3
class Chien:
    @staticmethod
    def definition():
        return "Le Chien (Canis lupus familiaris) est la sous-espèce domestique de Canis lupus (Loup gris)."
```

> Les méthode (d'instance) sont très utilisées sur la programmation objet en python. Les méthodes de classe sont très utiles mais sont utilisées plus rarement. Les méthodes statiques sont à éviter.

Il est possible de faire hériter les classes. Cela permet de réutiliser des méthodes et variables.
```python3
class Animal:
    nb_pattes = 4

class Chat(Animal):  # Chat classe fille et Animal classe mère (ou classe parent)
    def __init__(self, nom):
        self.nom = nom

    def info(self):
        print(f"{self.nom} a {self.nb_pattes} pattes.")

felix = Chat("Felix")
felix.info()  # => Felix a 4 pattes.
```

Il est possible de redéfinir une fonction héritée (surcharger), cela cache la fonction de la classe mère.
```python3
class Animal:
    def info(self):
        print("C'est un animal")

class Chien(Animal):
    def info(self):
        print("C'est un canidé")

chien = Chien()
chien.info()  # => C'est un canidé
```

Afin d'accéder à la classe parent, il est possible d'utiliser `super()`.
```python3
class Animal:
    def info(self):
        print("C'est un animal")

class Chien(Animal):
    def info(self):
        super().info()
        print("C'est un canidé")

chien = Chien()
chien.info()  # => C'est un animal\nC'est un canidé 
```

 
```python3
class Rectangle:
    def __init__(self, longueur, largeur):
        self.longueur = longueur
        self.largeur = largeur
    
    def aire(self):
        return self.longueur * self.largeur

class Carre(Rectangle):
    def __init__(self, cote):
        super().__init__(cote, cote)

carre = Carre(5)
print(carre.aire())  # => 25
```

Bien qu'a éviter, il est possible de faire de l'héritage multiple en python (car obligé dans certains cas spécifiques).
```python3
class Rectangle:
    def __init__(self, longueur, largeur):
        self.longueur = longueur
        self.largeur = largeur
    
    def aire(self):
        return self.longueur * self.largeur

class Losange:
    def __init__(self, longueur, largeur):
        self.longueur = longueur
        self.largeur = largeur
    
    def perimetre(self):
        return self.longueur * 2 + self.largeur * 2

class Carre(Rectangle, Losange):
    def __init__(self, cote):
        super().__init__(cote, cote)

carre = Carre(5)
print(carre.aire())  # => 25
print(carre.perimetre())  # => 20
```

En cas de surcharge de fonction entre classes mères, la première classe dans l'héritage l'emporte (cela était deja le cas pour le constructeur dans l'exemple, ci-dessus).
```python3
class Rectangle:
    def __init__(self, longueur, largeur):
        self.longueur = longueur
        self.largeur = largeur
    
    def aire(self):
        return 3

class Losange:
    def __init__(self, longueur, largeur):
        self.longueur = longueur
        self.largeur = largeur
    
    def aire(self):
        return self.longueur * self.largeur

class Carre(Rectangle, Losange):
    def __init__(self, cote):
        super().__init__(cote, cote)

carre = Carre(5)
print(carre.aire())  # => 3
```

Il est possible de définir des getter et setter via des méthodes `set_[varname]` et `get_[varname]`. Néanmoins cela n'est pas 'pythonic'. Le mécanisme suivant est le standard au sein des développements python: 
```python3
class User:
    def __init__(self, username, password):
        self._username = username  # _username est la variable 'cachée'
        self._password = password  # _password est la variable 'cachée'
    
    @property  # creation de la property 'username', créer le getter
    def username(self):
        return f"user:{self._username}"  # modifie afin de renvoyer user:[valeur variable 'cachée']
    
    @username.setter  # créer le setter sur la property username définie au dessus
    def username(self, value):
        if value.lower() == value:  # control que l'username est en minuscule
            self._username = value  # met a jour la variable cachée
        else:
            print("L'username doit être en minuscules !")
    
    @property  # creation de la property 'password', créer le getter
    def password(self):
         return self._password  # ce getter ne modifie pas la valeur et renvoie directement la variable 'cachée'
    
    @password.setter
    def password(self, value):
        if len(value) > 4:  # vérifie que le mot de passe fait plus de 4 caractères
            self._password = value
        else:
            print("Mdp trop court")

paul = User("paul", "azerty")

print(paul.username)  # => user:paul
paul.username = "Pg"  # => L'username doit être en minuscules !
print(paul.username)  # => user:paul
paul.username = "pg"
print(paul.username)  # => user:pg

print(paul.password)  # => azerty
paul.password = "toto"  # => Mdp trop court
print(paul.password)  # => azerty    
```

### 9. Gestion des erreurs
Lorsque python rencontre une erreur il déclenche (lève) une exception. Lorsqu’une exception est déclenchée dans notre code et qu’elle n’est pas gérée, le programme s’arrête. Une exception peut être gérée en utilisant un `try-except` (souvent appelé `try-catch` dans d’autres langages). Les exceptions déclenchées par une fonction doivent/sont documentées dans les documentations des modules: pour l'api gitlab (https://python-gitlab.readthedocs.io/en/stable/api/gitlab.html) la méthode `get_license` peut lever (raise) les exceptions `GitlabAuthenticationError` ou `GitlabGetError`. 
```python3
liste = [1, 2, 3, 4]
try:
    liste[10]  # out of range
except IndexError:
    print("Index en dehors de la liste")

print("Le programme continue car l'erreur a été traitée")
```

Plusieurs exceptions peuvent être traitées en multipliant les `except`.
```python3
liste = [1, 2, 3, 4]
try:
    liste[1] = 99
    liste["deux"] = 999
except IndexError:
    print("Index en dehors de la liste")
except TypeError:
   print("L'indice n'est pas un nombre !")

print("Le programme continue car l'erreur a été traitée")
```

Les exceptions sont des objets (donc des instanciations d'une classe). Le *keyword* `except` prend le nom de la classe de l'exception qui peut être levée.  Il compare l'exception levée et ses classes parentes avec l'exception attendue. Les classes des exceptions héritent toutes de la classe de base `Exception`. Ainsi pour gérer n'importe quelle exception, il est possible de faire:
```python3
liste = [1, 2, 3, 4]
try:
    liste[10] = 99
except Exception:
    print("Une erreur est survenue")
```
Mais cela est déconseillé car cela indique une non maitrise du code.

Nous pouvons ainsi créer nos propres erreurs en héritant de `Exception`. L'exception peut être levée grace au *keyword* `raise`.
```python3
class PasswordPasConforme(Exception):
    def __init__(self, password):
        msg = f"Le mdp {password} n'est pas conforme < 5"  # défini un message d'erreur custom
        super().__init__(msg)

class User:
    def __init__(self, username, password):
        if len(password) < 5:
            raise PasswordPasConforme(password)
        
        self.username = username
        self.password = password

try:
    paul = User("paul", "toto")
except PasswordPasConforme as e:  # 'as' permet de renommer l'erreur dans l'objet 'e', c'est un 'alias'
    print(e)
```

### 10. Fichiers
Pour lire l'ensemble des lignes d'un fichier
```python3
# "r" pour lecture
# "w" pour ecriture
# "w+" pour lecture/ecriture
# "a" ajouter a la fin (append)
file1 = open("text.txt", "r")  # ouvre un fichier en lecture et stocke le descripteur de fichier dans la variable file1.

content = file1.readlines()  # lecture de l'ensemble des lignes du fichers
print(content)

print("content:")
print(content)
for line in content:
    print(line, end="")

file1.close()  # il faut fermer le descripteur de fichier a la fin du traitement afin de liberer les ressources du système.
```

Pour ecrire des lignes dans un fichier
```python3
file2 = open("text2.txt", "r")
# lines = ["Bonjour\n", "Comment allez vous ?\n"]
file2.writelines(lines)
file2.close()
```

Afin d'eviter les oublis de fermeture de descripteur de fichier, le *keyword* `with` a été ajouté et permet de systématiquement fermer les descripteurs une fois sorti du bloc associé.
```python3
lines = ["Bonjour\n", "Comment allez vous ?\n"]
with open("text2.txt", "w") as f:
    f.writelines(lines)

f.writelines(["derniere ligne\n"])  # => ERROR!
```

Pour lire une portion de texte, la méthode `read` est utilisée
```python3
with open("text.txt", "r") as f:
    content = f.read(1024)  # lecture de 1024 bytes
    print(content)
    print(f.tell())  # indique la position actuelle du curseur de lecture
    print(f.seek(0))  # déplace le curseur de lecture à la position 0
```

Pour ecrire une portion de text, la méthode `write` est utilisée
```python3
with open("text.txt", "w") as f:
    f.write("Bonjour, comment allez vous ?")
    print(f.tell())  # indique la position actuelle du curseur d'écriture
    print(f.seek(9))  # déplace le curseur d'écriture à la position 9
    f.write("hello")
    f.flush()  # assure que les modifications sont poussées dans le fichier (par rapport au mécanisme de buffer)
```
Le "flush" fait référence à l'action de vider le tampon de sortie associé à un flux de fichiers. Lorsque vous écrivez des données dans un fichier à l'aide de fonctions, ces données sont généralement stockées dans un tampon de sortie temporaire (buffer) plutôt que d'être écrites immédiatement sur le disque.

Le tampon de sortie a pour objectif d'optimiser les performances en réduisant le nombre d'opérations d'écriture sur le disque, qui sont relativement coûteuses en termes de temps. Plutôt que d'effectuer une écriture à chaque appel de fonction d'écriture, les données sont accumulées dans le tampon jusqu'à ce qu'il soit plein ou que vous effectuiez explicitement un "flush".

Le "flush" consiste à vider le tampon de sortie, ce qui force l'écriture immédiate des données dans le fichier. Cela peut être utile dans certaines situations, notamment lorsque vous devez vous assurer que les données écrites sont immédiatement disponibles pour d'autres processus ou pour vous-même lorsque vous lisez à partir du fichier.

11. Virtual Environnement
Afin de remédier aux problèmes de conflit de dépendance, python utilise un mécanisme dit d'environnement virtuel (par abus de langage, car aucun processus de virtualisation ou de conteneurisation n'est appliqué). Cela est similaire au `node_modules` de npm.

L'environnement  virtuel peut être créé par la commande
```bash
# python -m venv [non du dossier, le standard pour le nom de dossier est venv]
$ python -m venv venv
```

Pour entrer (activer) l'environnement virtuel. La ligne de commande (PS1) est modifiée pour ajouter `(venv)` au debut une fois l'activation réussie
```bash
$ source venv/bin/activate
(venv) $ 
```

Pour installer un package dans l'environnement virtuel:
```bash
(venv) $ pip install flask
```

Pour sortir de l'environnement virtuel:
```bash
(venv) $ deactivate
$
```

## Cours - Programmation réseau
### 1. Socket
La bibliothèque socket en Python est une bibliothèque standard qui fournit des fonctionnalités permettant la communication réseau. Elle permet de créer des applications réseau en utilisant les protocoles TCP/IP.

La bibliothèque socket offre une interface de programmation bas niveau pour la communication réseau. Elle permet de créer des sockets (qui sont essentiellement des points d'interface de communication) permettant d'établir des connexions réseau, d'envoyer et de recevoir des données.

L'architecture client-serveur est un modèle de conception dans lequel les tâches d'une application sont réparties entre deux entités distinctes : le client et le serveur. Ces deux entités communiquent entre elles via un réseau, généralement en utilisant le protocole TCP/IP (d'où l'intervention de socket).

Le client est l'entité qui envoie des requêtes au serveur et reçoit les réponses. Il est généralement une application ou un navigateur Web.

Le serveur est l'entité qui reçoit les requêtes des clients, traite ces requêtes et renvoie les réponses appropriées. Il est généralement une application ou un ordinateur dédié qui fournit des services spécifiques aux clients.

Documentation: https://docs.python.org/3/library/socket.html

Pour creer un client avec socket:
```python3
# ./client.py
import socket

s = socket.socket()  # creer l'objet (le descripteur) socket

s.connect(("127.0.0.1", 8888))  # demande a la socket de se configurer en 'client' et se connecter au serveur 127.0.0.1 port 8888. Si aucun serveur en écoute sur le port 8888 sur l'ordinateur 10.10.10.2 une erreur est renvoyée
s.sendall("Bonjour serveur, je suis client\n".encode())  # envoie la chaine de caractère à l'adresse choisie ci-dessous
s.close()  # le descripteur doit etre fermé afin d'éviter de monopoliser les ressources du système
```

Pour creer un serveur avec socket:
```python3
# ./serveur.py
import socket

s = socket.socket()  # creer l'objet (le descripteur) socket

# Pour faire un serveur qui écoute
s.bind(("127.0.0.1", 8888))  # configure l'adresse où écouter (sur l'ordinateur) et le port d'écoute
s.listen()  # lance l'écoute et l'attente de connexion sur l'adresse et le port configuré précédemment

# Pour accepter une nouvelle connexion
connexion, address = s.accept()  # connexion est de descripteur de la connexion 

print(f"Connexion arrivant depuis {address}")
content = connexion.recv(1024).decode()  # lecture de 1024 bytes envoyé (ou moins)
print(content)
connexion.close()  # le descripteur doit etre fermé afin d'éviter de monopoliser les ressources du système
s.close()  # le descripteur doit etre fermé afin d'éviter de monopoliser les ressources du système
```

Ainsi le serveur peut être lancé en premier
```bash
python ./serveur.py
```
Puis le client
```bash
python ./client.py
```

L'exemple ci dessus traite le cas d'un client envoyant des données et d'un serveur réceptionnant et affichant ces données. Cela peut etre modifié afin que :
1. le client envoie des données
2. le serveur recoit des données
3. le serveur renvoie une réponse
4. le client recoit la réponse
```python3
# ./client.py
import socket

s = socket.socket()  # creer l'objet (le descripteur) socket

s.connect(("127.0.0.1", 8888))  # demande a la socket de se configurer en 'client' et se connecter au serveur 127.0.0.1 port 8888. Si aucun serveur en écoute sur le port 8888 sur l'ordinateur 10.10.10.2 une erreur est renvoyée
s.sendall("Bonjour serveur, je suis client\n".encode())  # envoie la chaine de caractère à l'adresse choisie ci-dessous
response = s.recv(1024).decode()
print(response)
s.close()
```
```python3
# ./serveur.py
import socket

s = socket.socket()  # creer l'objet (le descripteur) socket

# Pour faire un serveur qui écoute
s.bind(("127.0.0.1", 8888))  # configure l'adresse où écouter (sur l'ordinateur) et le port d'écoute
s.listen()  # lance l'écoute et l'attente de connexion sur l'adresse et le port configuré précédemment

# Pour accepter une nouvelle connexion
connexion, address = s.accept()  # connexion est de descripteur de la connexion 

print(f"Connexion arrivant depuis {address}")
content = connexion.recv(1024).decode()  # lecture de 1024 bytes envoyé (ou moins)
print(content)
connexion.sendall("Bonjour client, je suis le serveur\n".encode())
connexion.close()  # le descripteur doit etre fermé afin d'éviter de monopoliser les ressources du système
s.close()  # le descripteur doit etre fermé afin d'éviter de monopoliser les ressources du système
```

### 2. Request (Bonus non vu en cours)
> Ce sujet n'a pu être abordé en cours, mais cette section pourra vous être utile, notamment dans le cadre d'un projet rpi ;)

La bibliothèque requests en Python est une bibliothèque populaire utilisée pour effectuer des requêtes HTTP de manière simple et conviviale. Elle facilite l'interaction avec les API Web et la récupération de données à partir de serveurs.

La bibliothèque requests simplifie la gestion des requêtes HTTP en fournissant une interface élégante et intuitive pour envoyer des requêtes et traiter les réponses. Elle permet d'effectuer des requêtes HTTP GET, POST, PUT, DELETE, etc., et prend en charge diverses fonctionnalités telles que les en-têtes personnalisés, les paramètres de requête, les cookies, les sessions, les redirections, les certificats SSL, etc.

Request se base sur urllib, lui même se basant sur socket (en mode client).

Documentation: https://requests.readthedocs.io/en/latest/

Pour effectuer une requête GET :
```python3
import requests

res = requests.get('https://google.com')

print(res)
print(res.status_code)  # => 200, affiche le code de la réponse
print(res.headers)  # => affiche les entêtes HTTP de la réponse
print(res.text)  # => affiche le corps de la réponse
print(res.json())  # => essaie de convertir la réponse en JSON, peut envoyer une erreur si la réponse n'est pas un JSON

params = {
    "client": "firefox-b-d",
    "q": "it-akademy"
}
res2 = requests.get('https://google.com', params=params)  # effecture requete avec les paramètres GET
```

Pour effectuer une requête POST :
```python3
import requests

data = {
    "jsonKey": "JsonValue"
}

res = requests.post('https://httpbin.org/post', data=data)
print(res)
```

### 3. flask
Flask est un framework Web minimaliste écrit en Python. Il est conçu pour être simple, flexible et facile à utiliser, tout en offrant les fonctionnalités essentielles pour le développement d'applications Web. Flask permet de construire des applications Web rapidement et efficacement.

Documentation: https://flask.palletsprojects.com/en/2.3.x/

Pré-requis:

a. Creer un environnement virtuel
```bash
python -m venv venv
```
b. activer l'environnement virtuel
```bash
source venv/bin/activate
```
c. Installer flask
```bash
pip install flask
```
d. Definir le nom de l'application
```bash
export FLASK_APP=app
```
e. Définir le mode développement
```bash
export FLASK_DEBUG=true
```

Utiliser `setx [NOM] [Valeur]` pour windows à la place de `export [NON]=[Valeur]` de unix.

1. Pour créer un simple serveur flask
```python3
# ./app.py
app = Flask("app")

@app.route("/")
def root():
    return "Hello World !"
```

Le serveur flask peut être lancé via
```bash
flask run
```
Le résultat peut etre visualisé en allant sur http://127.0.0.:5000/

2. Pour utiliser des paramètres dans l'url
```pyton3
from markupsafe import escape  # afin d'encoder les données saisies par l'utilisateur
from flask import Flask

app = Flask("app")

@app.route("/bonjour/<name>")  # un paramètre dans l'url est une string
def bonjour(name):
    return f"Bonjour {escape(name)}"

@app.route("/test/<int:chiffre>/<int:dizaine>/")  # int: permet de convertir le type du paramètre
def test(chiffre, dizaine):
    return f"Bonjour {escape(chiffre + dizaine)}"
```
http://127.0.0.1:5000/bonjour/paul
http://127.0.0.1:5000/test/1/20/

3. Pour utiliser des arguments GET
```python3
from flask import Flask, request

app = Flask("app")

@app.route("/get")
def get():
    user = request.args.get("user")  # get ici est la méthode python pour récupérer l'argument, cela n'entre pas en compte avec la methode GET HTTP
    return f"Argument user: {user}"
```
http://127.0.0.1:5000/get?user=Paul

4. Pour utiliser des arguments POST
```python
from flask import Flask, request

app = Flask("app")

@app.route("/form")
def form():
    return """
    <form action="/submit" method="POST">
        <input type="text" name="data">
        <input type="submit" value="Envoyer">
    </form> 
    """

@app.route("/submit", methods=["GET", "POST", "PUT"])  # par défaut la méthode autorisée sur une route est GET, ici on autorise GE, POST et PUT
def submit():
    if request.method == "GET":
        return "Utilisation d'une méthode GET"
    elif request.method == "POST":
        data = request.form.get("data")
        return f"Method post: {data}"
```
http://127.0.0.1:5000/form

5. Renvoyer un JSON
```python3
from flask import Flask, jsonify

app = Flask("app")

@app.route("/json")
def jsonFunc():
    data = {
        "data": "ma data",
        "toto": ["une autre data", "dans un array"]
    }
    return jsonify(data)
```
http://127.0.0.1:5000/json


