---
title: "UT2004 installation help ubuntu 8.04"
date: 2008-05-18
forum: Gaming &amp; Leisure
---

### Post by OLIAX on 2008-05-18
I have UT2004 on dvd and I clicked linux-installer.sh it gets to past the EULA and then asked me if I accept the agreement I click yes and it says no write permission to /usr/local/games/ut2004

how do I enable it to run

---

### Post by noerrorsfound on 2008-05-18
Try to pick a different installation path, or run it with sudo.

cd to the directory the installer is in and then:
```
sudo ./linux-installer.sh
```
It's saying it needs admin rights to install to that system directory. I'd just install to my home folder.

---

### Post by OLIAX on 2008-05-18
im an ex windows user I have experience with command lines but what you just said made me think wtf?
can you explain that in basic terms that I (a linux noob) can understand?

---

### Post by xer0kill on 2008-05-18
Open up a terminal (Applications -- Accessories -- Terminal). cd to the directory where the file is stored. then type this:
```
sudo ./name-of-the-installer-file
```

---

### Post by OLIAX on 2008-05-19
> **xer0kill said:**
> Open up a terminal (Applications -- Accessories -- Terminal). cd to the directory where the file is stored. then type this:
```
sudo ./name-of-the-installer-file
```

I understand the command line part it's the part and I know how to use the terminal but where you said cd to the location that I don't know how to do

---

### Post by Perfect Storm on 2008-05-19
cd = **c**hange **d**irectory

eg. If the file is on your Desktop
**cd ~/Desktop**

eg. the file is in a folder in your directory
**cd <folder name>**

More info:
```
man cd
cd --help
```

---

