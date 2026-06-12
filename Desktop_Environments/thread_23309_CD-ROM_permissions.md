---
title: "CD-ROM permissions"
date: 2005-04-01
forum: Desktop Environments
---

### Post by Karlos on 2005-04-01
I have been trying to work out how to change the permissions for my cd rom

whenever I get some files off my cd I then have to go through all the files and give them write permissions..

I would like to be able to change the default settings...

I have consulted the IRC channel (#ubuntu) and was told to read the man pages about chmod..

which I did....but....

I didn't understand a word of it

..Any suggestions from my fellow ubuntu comrades would be much appreciated

Karlos

---

### Post by nix4me on 2005-04-01
Files copied from cd are always read only.

copy them into a folder and then do

chmod -R 755 /folder

---

### Post by Karlos on 2005-07-14
cheers . that's better

---

