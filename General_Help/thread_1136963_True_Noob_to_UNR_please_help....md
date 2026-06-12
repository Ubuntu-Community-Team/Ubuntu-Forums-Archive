---
title: "True Noob to UNR please help..."
date: 2009-04-25
forum: General Help
---

### Post by ooknmoo on 2009-04-25
I installed UNR on my Acer One everything is running.. what im trying to figure out is i want a couple 3rd party applications and when I download them they have directions on the notepad doc say extract, and run script. So I assume they mean in root terminal. So I unlocked terminal (which took me forever) and log in as root, got terminal to open and it says something about SUDO so i type sudo and the script line.. but that doesnt do anything. So my question is this... can someone give me an example of how to run a script and when you do.. does it make it possible to run the program scripted auto? and how do you make an icon and permanent link to run the program on the main screen for it. I apoligze in advance to the experienced people who are just reading this shaking thier heads...

---

### Post by Seks on 2009-04-25
sounds like you are trying to compile programs, this isn't necessary if you can find a .deb package (but I suspect most everyone tries it when they are first introduced to linux, thinking it's the only way :()

Which programs are they? if they are available when you search for them in synaptic, that's the best case scenario, as they can update themselves later. If not, check to see if the site you downloaded from provides debs or deb repositories.

---

### Post by ooknmoo on 2009-04-25
the first one i tried was office and then read and found out how to find applications in the repository.. but then I ran across my first one with Azureus Vuze.. they have a linux version to download and then extract..ect... 

It says to run script : 'azureus'; ex. "./azureus"    which makes no sense to me tried to copy and paste it in terminal with and without sudo before it... but i dont know what the hell im doin.

---

### Post by Seks on 2009-04-25
azureus is available in the ubuntu repos, search for vuze in add/remove (make sure "all available applications" is selected)

---

### Post by blackened on 2009-04-25
Azureus is available in the repositories. Not sure if it is the most bleeding-edge version or not.

```
sudo apt-get install azureus
```

---

### Post by calebk on 2009-04-25
Yes, the best and easiest way of installing software in Ubuntu is through add and remove programs. Just click, accessories and Add/Remove. Then just search for it! 

If you want a more updated version then sometimes you have to download it from their website. Make sure you are downloading a linux ubuntu .deb file. You can not install windows applications on ubuntu! You can install a piece of software called wine to install windows applications but this doesn't always work well

I tried downloading vuze and they only offer a .tar file and not a .deb file. You will definately struggle downloading that file. All you need to do is go to add/remove and download it from there, simple.

---

### Post by blackened on 2009-04-25
> **calebk said:**
> I tried downloading vuze and they only offer a .tar file and not a .deb file. You will definately struggle downloading that file. All you need to do is go to add/remove and download it from there, simple.

If I remember right, Azureus is written in java, so you'll need the java runtimes for it to work.

The download from the Azureus website comes with an installer script, so installation should be as simple as downloading, extracting, and running the install script from the terminal.

---

