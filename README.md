# DownloadMusic
Le script *downloadmp3.sh* télécharge l'audio de une ou plusieurs musiques Youtube, SoundCloud et autres, en format mp3 et les place dans des dossiers selon une certaine arborescence.

Optionnellement, il permet d'ajouter une image de couverture à ces musiques, qui sera visible selon votre lecteur mp3. 

De plus, il est possible de renseigner d'autres informations aux musiques téléchargées comme l'album et l'artiste (utile à la création de l'arborescence), le genre ou encore la date.

*downloadmp3.sh* intègre de façon automatique le titre des musiques comme titre des mp3, mais parfois le titre contient des expressions inutiles, qui peuvent être supprimées.

On peut aussi choisir d'extraire directement le nom de l'artiste si le titre est de la forme *"artiste - titre musique"*.

### Installation

**L'exécution des scripts doit se faire dans un shell bash**

Ouvrir un terminal **bash** et se placer dans le dossier téléchargé, installer *downloadmp3* avec:
```bash
sudo ./install.sh
```
*downloadmp3* utlise les paquets *youtube-dl*, *ffmpeg* et *mid3v2*, donc s'ils ne sont pas installés, le script d'installation s'en occupe. 

Pour désinstaller le programme, exécuter:
```bash
sudo ./uninstall.sh
```
Les paquets *youtube-dl*, *ffmpeg* et *mid3v2* peuvent aussi être désinstallés.

Pour vérifier l'installation, afficher l'aide avec:
```bash
downloadmp3 -h
```

### Utilisation

Le script stocke les musiques téléchargées et traitées de cette manière:
```
dossier
└── Artiste
    └── Album
        └── titre1.mp3
        └── ...       
```

- **Mode normal**

`downloadmp3 -i /chemin/absolu/image -u URL -d /chemin/absolu/dossier -a "Artiste" -A "Album" -g "Genre" -y année -r "expr1/expr2/.../exprN"`

- **Mode extract**

A utiliser si le titre des musiques ressemble à *"artiste - titre musique"*

`downloadmp3 -i /chemin/absolu/image -u URL -d /chemin/absolu/dossier -e -A "Album" -g "Genre" -y année -r "expr1/expr2/.../exprN"`

### Etapes
1. Choisir une playlist ou une musique sur un [site géré par youtube-dl](https://github.com/ytdl-org/youtube-dl/tree/master/youtube_dl/extractor)
2. Télécharger une image de couverture de l'album si besoin
3. Ouvrir un terminal **bash**
5. Lancer le script avec les options choisies en fonction des titres des musiques
6. Vérifier le téléchargement avec votre lecteur mp3 préféré

### Exemples

- **Minimal**

`downloadmp3 -u URL`
```
.
└── Inconnu
    └── Inconnu
        └── Georges_Brassens_Les_copains_d´abord.mp3
        └── ...       
```

- **Artiste et Album**

`downloadmp3 -u URL -a "Georges Brassens" -A "Le meilleur de Brassens" `
```
.
└── Georges Brassens
    └── Le meilleur de Brassens
        └── Georges_Brassens_Les_copains_d´abord.mp3
        └── ...       
```

- **Dossier de stockage**

`downloadmp3 -u URL -d "/home/user/Musique"`
```
Musique
└── Inconnu
    └── Inconnu
        └── Georges_Brassens_Les_copains_d´abord.mp3
        └── ...       
```
- **Intégrer des informations aux mp3**

`downloadmp3 -u URL -a "Georges Brassens" -A "Le meilleur de Brassens" -g "Chanson française" -y 2019`

*Note: Par défaut, l'artiste, l'album et le genre sont* "Inconnu" *et date est* 0000.

- **Renseigner des expressions à supprimer des titres**

`downloadmp3 -u URL -r "(audio)/lyrics/live"`

Cela enlèvera toute occurence des expressions *"(audio)"*, *"lyrics"* et *"live"*, **sans être sensible à la casse**.

*Note: Par défaut seule l'expression* " - " *est enlevée (en général utilisée pour séparer l'artiste du titre).*


### Contact
Pour rapporter un bug ou tout commentaire, vous pouvez me joindre par:
- Mastodon: rafutek@mamot.fr
- Diaspora*: rafutek@framasphere.org
- Mail: rafutek@protonmail.com