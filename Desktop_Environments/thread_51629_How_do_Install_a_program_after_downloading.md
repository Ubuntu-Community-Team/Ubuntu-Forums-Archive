---
title: "How do Install a program after downloading"
date: 2005-07-24
forum: Desktop Environments
---

### Post by Jhodytropical on 2005-07-24
Hi,

 I wonder how to install a program (eg. Firefox) after saving it on my disk !!!

---

### Post by Takis on 2005-07-24
[QUOTE=Jhodytropical]Hi,

 I wonder how to install a program (eg. Firefox) after saving it on my disk !!![/QUOTE]
You shouldn't need to download Firefox, you should be able to use Synaptic to install it.
GUI instructions:
Synaptic->World Wide Web->mozilla-firefox->left-click and hit 'Mark for Installation'. In one of the top menu bars, hit 'Apply'.
Command line instructions:```
sudo apt-get install mozilla-firefox
```
Alternatively, if you've downloaded the Firefox source code (usually in a tar.gz or tar.bz2 file), extract it to a temporary directory, open a terminal, cd to the directory, and then type:
```
./configure
make
sudo make install
```
You may want to see if there's a readme file in the directory before running these commands. Although they're reasonably generic, some installers use different ones, and a readme would detail how to use it.

---

