---
title: "ubuntu program pychess won't open"
date: 2017-02-08
forum: Gaming &amp; Leisure
---

### Post by newblank25 on 2017-02-08
i went to pychess in ubuntu software and downloaded it. i got the icon but when I click on it then it just blinks and doesn't open. Any help would be appreciated.THX

---

### Post by thehipho on 2017-02-08
What's the program output if you run it from the terminal?
```
pychess
```

---

### Post by deadflowr on 2017-02-09
*Thread moved to **Gaming & Leisure**.*

Which release of Ubuntu? (14.04, 16.04 other?)

---

### Post by howefield on 2017-02-09
I'd suggest installing the current version which you can get from the pychess website : [http://www.pychess.org/download/](http://www.pychess.org/download/) 

Download the relevant .deb packages and install.

---

### Post by newblank25 on 2017-02-09
ubuntu software center downloads pychess but when clicking on icon in launcher it only flashes but won't open. if i download it from site what is the syntax to use in terminal to get to work.is it java-jar home/download/pychess

---

### Post by QIII on 2017-02-09
Threads merged.

---

### Post by newblank25 on 2017-02-09
used sudo update the sudo install pychess still only icon comes on but nothing else. i'm using ubuntu 16.04 64 bit also went to pychess saw download but that didn't work either

---

### Post by howefield on 2017-02-10
> **newblank25 said:**
> used sudo update the sudo install pychess still only icon comes on but nothing else. i'm using ubuntu 16.04 64 bit also went to pychess saw download but that didn't work either

To download the deb files you could use, from the terminal..

```
wget http://www.pychess.org/download/pychess_0.12.4-1_all.deb -P ~Downloads
```
```
wget http://www.pychess.org/download/python3-pychess_0.12.4-1_all.deb -P ~/Downloads
```

and to install them, again from the terminal..

```
sudo apt install ~/Downloads/python3-pychess_0.12.4-1_all.deb
```
```
sudo apt install ~/Downloads/pychess_0.12.4-1_all.deb
```

I'd uninstall the current version of pychess before installing the new one..

```
sudo apt purge pychess
```

You might also simulate the package installations using the -s option just to make sure that you won't get any errors, eg on dependencies before you do the actual install.

```
sudo apt install -s ~/Downloads/python3-pychess_0.12.4-1_all.deb
```
```
sudo apt install -s ~/Downloads/pychess_0.12.4-1_all.deb
```

---

