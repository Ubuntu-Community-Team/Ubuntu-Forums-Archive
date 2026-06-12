---
title: "Remove everything Gnome installs?"
date: 2007-08-29
forum: Desktop Environments
---

### Post by ale1981 on 2007-08-29
Hi, 

I installed Ubuntu Server edition but wanted a desktop GUI while i was learning. I am now at a stage where i dont need the desktop GUI anymore, but unfortunately i used sudo apt-get instead of sudo aptitude when installing it so I am left with a lot of apps that I dont need, is there any way to get rid of all the programs that were installed along with ubuntu desktop?


Thanks.

---

### Post by jclmusic on 2007-08-29
try ```
sudo apt-get autoremove
``` which will automatically remove any unused dependencies.

---

### Post by ale1981 on 2007-08-29
Tried that, I get;

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 66 not upgraded.

```

for some reason it still thinks they are all needed, i have removed ubuntu-desktop.

---

### Post by toasterofirony on 2007-08-29
Daft question, I'm sure, but why do you want to get rid of gnome? Why not just boot into the CLI? I mean, in this day and age the few megs that gnome takes up on your HDD isn't that a big a deal, is it?

I'd advise hanging onto it, unless you really want to burn a bridge or somehow having the option of a gui is really going to cramp your nerd-fu.

---

### Post by ale1981 on 2007-08-29
> **toasterofirony said:**
> Daft question, I'm sure, but why do you want to get rid of gnome? Why not just boot into the CLI? I mean, in this day and age the few megs that gnome takes up on your HDD isn't that a big a deal, is it?

I'd advise hanging onto it, unless you really want to burn a bridge or somehow having the option of a gui is really going to cramp your nerd-fu.

No its nothing to do with any of them at all. Its the fact that when I use sudo apt-get upgrade I have to keep updating all the packages that come with the desktop to, which is a waste of time and bandwidth.

---

### Post by Wolki on 2007-08-29
Try removing gtk or the X server, pretty much everything should in the end depend on that so you'll remove most of the things. Then you can check the list of installed packages later and remove anything that might have slipped through.

---

### Post by ale1981 on 2007-08-29
> **Wolki said:**
> Try removing gtk or the X server, pretty much everything should in the end depend on that so you'll remove most of the things. Then you can check the list of installed packages later and remove anything that might have slipped through.

Thanks Wolki will give that a go.

---

