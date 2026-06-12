---
title: "Two things Ubuntu needs"
date: 2006-09-18
forum: Desktop Environments
---

### Post by DagonX on 2006-09-18
The first thing Ubuntu needs is some way to empty the trash. I moved a rather large directory to the trash. The only way I could empty the tash was to drillo down and change the permissions for every sub directory and file.

The second thing Ubuntu needs is a file manager that can work as root.

---

### Post by skymt on 2006-09-18
1. You mean empty the trash *as root*, right? Easy: "sudo rm -r ~/.Trash/*".
2. Also easy. Make a launcher that runs "gksudo nautilus".

---

### Post by Poeffie on 2006-09-18
1. Right-click the wastebasket: Empty the Wastebasket
2. what skymt said
(actually I found another way to do this, it had to do with a script that opened the target directory as root, but I've lost that since my update to 6.06)

Anything else you need?

---

### Post by Pjotr123 on 2006-09-18
> **DagonX said:**
> The first thing Ubuntu needs is some way to empty the trash. I moved a rather large directory to the trash. The only way I could empty the tash was to drillo down and change the permissions for every sub directory and file.

The second thing Ubuntu needs is a file manager that can work as root.

Ubuntu already has both!

Empty trash bin: rightclick trash bin, choose "empty".

file manager as root: open terminal screen, type "gksudo nautilus"
You can even make a menu entry for this command line.

Greeting, Pjotr.

---

### Post by fragos on 2006-09-18
If you don't always want the safety of the trash bin, you can tell Nautilus to add a delete option in addition to trash.

---

### Post by Ramses de Norre on 2006-09-18
Set this in a file in .gnome2/nautilus-scripts/Open\ as\ root
```
#!/bin/bash
gksudo -g "nautilus --no-desktop" $NAUTILUS_SCRIPT_CURRENT_URI
exit 0

```
You can then through right-click > scripts open the current folder as root.

---

### Post by declaration on 2006-09-18
Automatix can sort out opening and editing stuff as root via nautilus.

---

### Post by andiii on 2006-09-18
> **fragos said:**
> If you don't always want the safety of the trash bin, you can tell Nautilus to add a delete option in addition to trash.

Holding down Shift while pressing delete does that..

---

### Post by skymt on 2006-09-18
A lot of people here didn't read carefully enough. The OP said s/he needed to go through a folder changing permissions before the trash would empty. The sudo rm line would be perfect for that situation. Or, wait for Edgy (GNOME 2.16) which will finally have recursive permissions changes.

---

### Post by edm1 on 2006-09-18
these "problems" are both GNOME related not Ubuntu related anyway.

> **skymt said:**
> Or, wait for Edgy (GNOME 2.16) which will finally have recursive permissions changes.

i'm sure i've always been able to chmod -R to recursively change permissions.

---

### Post by skymt on 2006-09-18
> **edm1 said:**
> these "problems" are both GNOME related not Ubuntu related anyway. i'm sure i've always been able to chmod -R to recursively change permissions.

I meant in Nautilus, which should have been clear from my reference to GNOME 2.16. Sorry for any confusion.

---

### Post by BLTicklemonster on 2006-09-18
I'm using Kubuntu, and I just don't see a trash can anywhere....

---

### Post by WalmartSniperLX on 2006-09-19
LoL why not use the sudo rm -r command to delete if you're having super user probs

---

### Post by skymt on 2006-09-19
> **WalmartSniperLX said:**
> LoL why not use the sudo rm -r command to delete if you're having super user probs(Score: -1, Redundant)

---

