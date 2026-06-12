---
title: "!!!!!HELP HELP HELP With EMERALD!!!!!"
date: 2009-02-20
forum: General Help
---

### Post by ColemanK on 2009-02-20
I've installed Emerald Theme Manager, but it seems that the icon doesn't appear in any of my menus. I've searched 'emerald' and it comes up with three things: 'cp to usr-share-emerald-themes' (a folder), 'emerald-theme-manager (the app), and the icon for Emerald Theme Manager. When I click on the app, this is what comes up:

 'There was an error launching the application. Details: Failed to execute child process "emerald-theme-manager" (No such file or directory)'.

This is how I installed it when I did:
I went to this thread: [https://help.https://help.ubuntu.com/community/CompositeManager/CompizFusionubuntu.com/community/CompositeManager/CompizFusion](https://help.https://help.ubuntu.com/community/CompositeManager/CompizFusionubuntu.com/community/CompositeManager/CompizFusion), and followed these instructions: 


You can select different themes with the emerald-theme-manager tool. To download the themes for emerald You must first install subversion, then activate the theme repositories.

```

sudo apt-get install subversion
svn ls https://svn.generation.no/emerald-themes 

```

You can then use the "Fetch GPL'd themes" button of The "emerald-theme-manager" tool. 

Can you help me?```

```










Also, for some strange reason, and I don't know if this has anything to do with the problem, when I put the app into Text Edit, it seems to be all in French... Here it is:

```
[Desktop Entry]
X-AppInstall-Package=emerald
X-AppInstall-Popcon=15902
X-AppInstall-Section=universe

Type=Application
Name=Emerald Theme Manager
Name[ca]=Gestor de temes de l'Emerald
Name[de]=Emerald Motiv Manager
Name[es]=Gestor de temas del Emerald
Name[fr]=Gestionnaire de thèmes Emerald
Comment=Configure Emerald themes
Comment[ca]=Configureu els temes de l'Emerald
Comment[de]=Konfiguriert Emerald Motive
Comment[es]=Configura los temas del Emerald
Comment[fr]=Configurerer les options des thèmes Emerald
Icon=emerald-theme-manager-icon
Exec=emerald-theme-manager
Terminal=false
Categories=Settings;
MimeType=application/x-emerald-theme;
X-Ubuntu-Gettext-Domain=app-install-data
```

---

### Post by darco on 2009-02-20
What happens when you run the command in a terminal?

```
emerald
```

darco

---

### Post by mb_webguy on 2009-02-20
Wouldn't it be "emerald --replace"?

---

### Post by ColemanK on 2009-02-20
> **darco said:**
> What happens when you run the command in a terminal?

```
emerald
```

darco

This:

```
thehprock@thehprock-laptop:~$ emerald
The program 'emerald' is currently not installed.  You can install it by typing:
sudo apt-get install emerald
bash: emerald: command not found
thehprock@thehprock-laptop:~$ 
thehprock@thehprock-laptop:~$ 


```

And I can't uninstall it because it isn't found in 'Add/Remove...' .
Plus, all the files are locked. ALSO, when I try to reinstall it, it just says that I have the latest version, and don't need to install it...

---

### Post by darco on 2009-02-20
ya I think you are right..I know in ccsm its emerald --replace but I thought it was just emerald in a terminal

darco

p.s. trying installing via synaptics repos

---

### Post by mcduck on 2009-02-20
Both Emerald and Emerald Theme Manager are available in Ubuntus repositories. (You need to use Synaptic package Manager, the Add/Remove"-thing only has a small selection of most commonly used applications while Synaptic is the actual package management tool that handles *all* available packages.

Emerald Theme Manager can be started from System/Preferences/Emerald Theme Manager

Command "emerald --replace" would start Emerald itself, not the theme manager. Command for the theme manager is "emerald-theme-manager". Anyway, since you tried running "emerald" and got a response that it's not installed it seems like you only installed the theme manager, not the Emerald itself.

(I couldn't check what guide you used to install Emerald/Emerald Theme Manager, the link you posted isn't a correct URL. But it could easily be very outdated information and you are probably trying to do this harder way than what's really needed. To install Emerald & Emerald Theme Manager all you need to do is run "sudo apt-get install emerald emerald-theme-manager", or find those packages with Synaptic and install that way.)

---

