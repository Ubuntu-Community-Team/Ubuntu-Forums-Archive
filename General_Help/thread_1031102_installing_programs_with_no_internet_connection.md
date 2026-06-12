---
title: "installing programs with no internet connection"
date: 2009-01-05
forum: General Help
---

### Post by hermanikk on 2009-01-05
OK so I'm pretty new to Linux and I'm a bit frustrated with the difficulty of installing programs without an internet connection. It seems that "make" is not installed, and to get it I need to have my Linux computer online.
Is this so?
I have a Windows computer that will go online, but can't get online with Linux because I can't install anything.
Any help is appreciated, thanks.

---

### Post by iaculallad on 2009-01-05
For the 'make' command, be sure that you have your build-essential files. Open your terminal and we will set your CD/DVDROM as a source:

*Before issuing the terminal commands below, be sure that you've inserted you're Ubuntu LiveCD*

```
sudo apt-cdrom add
sudo apt-get install build-essential
```

---

