
# 🎮 Projet Java RMI — Game Server / Client

## ✅ Version Java utilisée

```bash
java version "1.8.0_31"
Java(TM) SE Runtime Environment (build 1.8.0_31-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.31-b07, mixed mode)
```

---

## ⚙️ Compilation

### 🔧 Compilation locale
```bash
javac -source 8 -target 8 server/*.java client/*.java common/*.java factory/*.java
```

### 🌐 Compilation pour exécution dynamique (codebase HTTP)
```bash
javac -source 8 -target 8 -d bin server/GameServer.java server/GameImpl.java server/GameSession.java client/ClientMain.java client/GameClient.java common/GameInterface.java common/PlayerCallback.java common/GameState.java factory/GameFactory.java
```


---

## 📁 Arborescence requise (serveur web)

Avant toute exécution, créez un dossier nommé `classes` à l'emplacement suivant, selon votre serveur web :

### 🌐 Si vous utilisez XAMPP (`htdocs`) :

Chemin complet :
```
C:\xampp\htdocs\classes\

classes/
├── client/
├── common/
├── factory/
└── server/

```

Commande pour copier les fichiers `.class` :

```bash
xcopy /s /y bin\client   C:\xampp\htdocs\classes\client
xcopy /s /y bin\server   C:\xampp\htdocs\classes\server
xcopy /s /y bin\common   C:\xampp\htdocs\classes\common
xcopy /s /y bin\factory  C:\xampp\htdocs\classes\factory
xcopy /s /y bin\security.policy  C:\xampp\htdocs\classes\
```

---

### 🐧 Si vous utilisez un serveur Apache sur Linux (`/var/www`) :

Chemin complet :
```
/var/www/classes/


classes/
├── client/
├── common/
├── factory/
└── server/

```

Commandes Linux correspondantes :

```bash
mkdir -p /var/www/classes/client
mkdir -p /var/www/classes/server
mkdir -p /var/www/classes/common
mkdir -p /var/www/classes/factory

cp -r bin/client/*   /var/www/classes/client/
cp -r bin/server/*   /var/www/classes/server/
cp -r bin/common/*   /var/www/classes/common/
cp -r bin/factory/*  /var/www/classes/factory/
cp bin/security.policy /var/www/classes/
```



---

## 🚀 Exécution

### 📡 Locale (fichiers accessibles localement)

#### 🪟 Sous Windows

```bash
java "-Djava.security.policy=security.policy" server.GameServer
java "-Djava.security.policy=security.policy" client.ClientMain
```

#### 🐧 Sous Linux

```bash
java -Djava.security.policy=security.policy server.GameServer
java -Djava.security.policy=security.policy client.ClientMain
```

---

### 🌍 Dynamique (chargement des classes via HTTP)

Remplacez `your@` par l’adresse IP ou le nom de domaine de votre machine (ex. : `http://192.168.1.10/classes/`)

#### 🪟 Sous Windows

```bash
java "-Djava.rmi.server.codebase=http://your@/classes/" "-Djava.security.policy=security.policy" server.GameServer
java "-Djava.rmi.server.codebase=http://your@/classes/" "-Djava.security.policy=security.policy" client.ClientMain
```

#### 🐧 Sous Linux

```bash
java -Djava.rmi.server.codebase=http://your@/classes/ -Djava.security.policy=security.policy server.GameServer
java -Djava.rmi.server.codebase=http://your@/classes/ -Djava.security.policy=security.policy client.ClientMain
```

---

## 🔍 Visualiser le registre RMI
Assurez-vous que le serveur est lancé, puis :


### 🪟 Sous Windows
```bash
java RegistryViewer localhost 1099
```

### 🐧 Sous Linux
```bash
java RegistryViewer localhost 1099
```
