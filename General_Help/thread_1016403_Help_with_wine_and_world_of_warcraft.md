---
title: "Help with wine and world of warcraft"
date: 2008-12-19
forum: General Help
---

### Post by Beautysdeath on 2008-12-19
WHile reading a how to guide on running World of warcraft from the windows partition on my harddrive, it stops short of tell how to get wine to do this anyone know how to make this work?

---

### Post by jerome1232 on 2008-12-19
Simply enable universe and install it with the package manager

System-Administration-Software Sources; Check the one with the word "Universe" in it.

Load synaptic and search for wine and mark it for installation

System-Administration-Synaptic Package Manager

gl

edit: just noticed your using xubuntu so the menu's may vary if you can't find them cli equivilants are:

```
sudo nano /etc/apt/sources.list
-----Hit ctrl+w and type "universe" no quotes then hit enter, should find the word universe
-----now uncomment the two lines that look like this (by deleting the # symbol)
#deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
----hit ctrl+o, then enter to save then ctrl+x to exit
sudo apt-get update
sudo apt-get install wine
```

---

### Post by Beautysdeath on 2008-12-19
universe not found? WIne is already installed if that helps more. Synaptic package manager found wine. wine-dev. wine-gecko. winefish

---

### Post by jerome1232 on 2008-12-19
> **Beautysdeath said:**
> universe not found? WIne is already installed if that helps more.

Oh, well then I'm not sure what the question is? You should just be able to double click the launcher.exe file to launch the game.

---

### Post by Beautysdeath on 2008-12-19
I am really new to linux. I have been opening my media file in my /dev/sda1 which is my windows partition via my file system in Ubuntu selecting program files from there which contains my WOW folder and clicking the launcher Icon I get a error that says this is not and archived file.

---

### Post by jerome1232 on 2008-12-19
Try right clicking it, selecting "open with other application" and locate wine and select that.

---

### Post by Beautysdeath on 2008-12-19
worked like a charm thanks alot man now to see if it actually will play right :)
I have one problem it seems to be running in a windowed mode I have bars to still switch between programs such as my applications and any other windows, terminals ect that I have open anyway to get that to go away?

---

