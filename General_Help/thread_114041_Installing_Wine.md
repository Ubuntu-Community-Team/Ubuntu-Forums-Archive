---
title: "Installing Wine"
date: 2006-01-07
forum: General Help
---

### Post by Y-town on 2006-01-07
Okay so im reading the directions on how to install wine for ubuntu [here]("http://www.winehq.com/site/download-deb") and im having some problems. There are three ways to download it right?

[LIST=1]
[*]Installing from the WineHQ APT Repository with Synaptic
[*]Installing from the WineHQ APT Repository with the console
[*]Building the Wine Package from Source using APT
[/LIST]

Which one of these would be the easiest for a noob to do?

---

### Post by Jammy_Stuff on 2006-01-07
Probably with synaptic. Go to System > Administration > Synaptic Package Manager and search for Wine. Install it.

---

### Post by ardchoille on 2006-01-07
[QUOTE=Y-town]Okay so im reading the directions on how to install wine for ubuntu [here]("http://www.winehq.com/site/download-deb") and im having some problems. There are three ways to download it right?

[LIST=1]
[*]Installing from the WineHQ APT Repository with Synaptic
[*]Installing from the WineHQ APT Repository with the console
[*]Building the Wine Package from Source using APT
[/LIST]

Which one of these would be the easiest for a noob to do?[/QUOTE]
Keep in mind that the recent Windows exploit is exploitable in wine too:
[http://blogs.zdnet.com/Ou/index.php?p=146](http://blogs.zdnet.com/Ou/index.php?p=146)

---

### Post by dcstar on 2006-01-07
[QUOTE=Jammy_Stuff]Probably with synaptic. Go to System > Administration > Synaptic Package Manager and search for Wine. Install it.[/QUOTE]
Do that, and also consider installing "winetools".

Straight after the wine install, in a terminal run "winecfg" to set up your environment.

---

