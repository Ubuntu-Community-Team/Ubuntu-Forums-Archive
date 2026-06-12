---
title: "Gnome shell in login preferences"
date: 2012-02-18
forum: Desktop Environments
---

### Post by Naddiseo on 2012-02-18
I've reinstalled ubuntu for the first time in a while, and was using gnome shell. After reinstalling ubuntu, I removed unity and installed gnome-shell, but on the login screen I get no option to use it. If I run `gnome-shell --replace` from the terminal it works. What am I missing?

---

### Post by forsubhi on 2012-02-18
try 

```
sudo apt-get install kubuntu-desktop 
```
 
to install kde desktop and see if it will appear in the login screen

---

### Post by Naddiseo on 2012-02-19
> **forsubhi said:**
> try 

```
sudo apt-get install kubuntu-desktop 
```
 
to install kde desktop and see if it will appear in the login screen

All I get for options is "gnome classic" and "gnome classic (no effects)".

---

### Post by Dreamer Fithp Apprentice on 2012-02-19
Did you follow whatever kind of messages the installer was throwing out during the installation or in the terminal while attempting to install kubuntu? I think if your system does not meet the minimum hardware specs for the new interface it will automatically install only the classic versions. I don't know, but perhaps a similar situation exists with respect to kubuntu.

---

### Post by Naddiseo on 2012-02-19
> **Dreamer Fithp Apprentice said:**
> Did you follow whatever kind of messages the installer was throwing out during the installation or in the terminal while attempting to install kubuntu? I think if your system does not meet the minimum hardware specs for the new interface it will automatically install only the classic versions. I don't know, but perhaps a similar situation exists with respect to kubuntu.

There were no such prompts. 

My machine definitely has more than the minimum specs; like I said, if I run `gnome-shell` from command line it works.

---

### Post by Naddiseo on 2012-02-20
Actually, it looks like the kde install didn't complete. I have now successfully installed it. KDM does show options for "Gnome"(-shell) login, but choosing the option gives an error about failing to load ubuntu. I'm starting to think that my problems are caused by me trying to use my second graphic card. I've had two identical cross-fired  graphics cards which, up until now, I've only had two monitors connected to.

---

### Post by Naddiseo on 2012-02-21
Figured it out. Uninstalling unity removes "gnome-session" which is what is needed to log into gnome-shell.

---

### Post by Krytarik on 2012-02-21
> **Naddiseo said:**
> Figured it out. Uninstalling unity removes "gnome-session" which is what is needed to log into gnome-shell.
Seems like you did it in exactly the order you've described it your OP then:
> **Naddiseo said:**
> After reinstalling ubuntu, I removed unity and installed gnome-shell
If you had installed "gnome-shell" before removing "unity", you wouldn't have had this issue in the first place; "gnome-session" depends, among other packages, on:
> **unity**[INDENT]Interface designed for efficiency of space and interaction. 
[/INDENT]or **unity-2d**[INDENT]Unity interface for non-accelerated graphics cards 
[/INDENT]or **gnome-shell** (>= 3.0)[INDENT]graphical shell for the GNOME desktop[/INDENT]Source: [http://packages.ubuntu.com/oneiric-updates/gnome-session](http://packages.ubuntu.com/oneiric-updates/gnome-session)

Regards.

---

### Post by Naddiseo on 2012-02-21
Having gnome-session depend on unity or gnome-shell seems backwards; I would have though it should be unity and gnome-shell that depend on gnome-session.

---

### Post by markbl on 2012-02-21
I don't understand why people decide to uninstall Unity just to use gnome-shell? It does not hurt to leave Unity installed, you don't have to log in to it, and removing it may cause problems like this.

---

