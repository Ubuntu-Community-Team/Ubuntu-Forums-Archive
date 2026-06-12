---
title: "is there an easy way install xwine or wine ?"
date: 2005-12-31
forum: Desktop Environments
---

### Post by bdd4 on 2005-12-31
i'm new to linux - using breezy 5.10.
anyone know an easy way of installing xwine or wine ?
need to run some windows applications. 
thx for your help.

bdd4

---

### Post by LoclynGrey on 2005-12-31
try [automatix]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix")

---

### Post by bdd4 on 2005-12-31
[QUOTE=LoclynGrey]try [automatix]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix")[/QUOTE]
thx i will
bdd4

---

### Post by pharcyde on 2005-12-31
You can add the wine apt repository from the official site by modifying **/etc/apt/sources.list**

Add the following two lines to the file:
[B]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/[/B]

Then type:
[B]sudo apt-get update
sudo apt-get install wine[/B]

You can also check out this page for more information:
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by bdd4 on 2006-01-01
i'm a little late in saying so but thank you for the help.
i like linux so much better than windows because of such great help.
years ago when i tried to call microsoft about problems iwas turned off
by their request to pay for support help if i did not have a contract with them.

thanks again -  bdd4

---

