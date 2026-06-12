---
title: "how to remove kubuntu-desktop"
date: 2011-04-14
forum: Desktop Environments
---

### Post by Praveen30 on 2011-04-14
i have downloaded kubuntu-desktop on my ubuntu desktop...i must it was very good but it is becoming very confusing for me to seprate out the gnome and kde packages..like if i am downloading something from torrent then by default kde torrent is downloading the file and it is on Gnome...huhhhh!!!

i have tried to remove it by-

sudo apt-get purge kubuntu-desktop..

but i am still getting the kde icon in my session after logout...and also i am getting different kubuntu packages....

---

### Post by XubuRoxMySox on 2011-04-14
Better to use **Synaptic**! Highlight _kubuntu-desktop_ and mark it for *complete* removal (all those Qt libraries as well as the applications).

-Robin

---

### Post by Copper Bezel on 2011-04-14
dixiedancer, kubuntu-desktop is a metapackage. Removing it doesn't do anything.

Praveen30, [select your current Ubuntu version here]("http://www.psychocats.net/ubuntu/puregnome") and run the provided command in terminal. Fairly *long* command. = )

Incidentally, dixiedancer, removing Qt libs and configuration apps is actually not necessarily a good thing. Configured properly, Qt settings can make KDE apps look native under Gnome. I highly recommend qt4-qtconfigure for this.

---

