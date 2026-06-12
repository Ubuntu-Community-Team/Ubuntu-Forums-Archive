---
title: "Can't uninstall KDE games, toys, JuK, Noatun..."
date: 2005-08-10
forum: Desktop Environments
---

### Post by mrowth on 2005-08-10
I'm new to Ubuntu. And to apt. And to Linux, I suppose.

I upgraded to KDE 3.4.2, which fixed the "duplicate file icons in a crash-happy Konqueror" issue. 

It's all fine now, except I have dozens of little KDE games, none of which I want. 

I'd also like to remove Noatun, JuK and Kaffeine unless any of them are required for anything -- I prefer MPlayer and Kaffeine crashes just about every time I open a new file.

But when I try to remove any of them, I can't because it wants to remove kde itself as well!

Example:
```
root@mybox:/home/myname # apt-get remove noatun*
Reading package lists... Done
Building dependency tree... Done
Note, selecting noatun-plugins for regex 'noatun*'
Note, selecting noatun for regex 'noatun*'
The following packages will be REMOVED:
  kde kdeaddons noatun noatun-plugins
0 upgraded, 0 newly installed, 4 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 8626kB disk space will be freed.
Do you want to continue [Y/n]?      

```
No, I don't think I want to continue. (Unless kde doesn't mean KDE.)

But since this wasn't a problem with SuSE (and since *This APT has Super Cow Powers*), I'll assume there's a way to get rid of the clutter anyway?

---

### Post by SGC on 2005-08-10
KDE is a meta package (read the description on synaptic) removing it will not remove kde itself.  It will only remove Noatun and it's plugins (Only 8 MB)

---

### Post by mrowth on 2005-08-10
Ah, thank you. That was helpful.

(Kynaptic pops up a tooltip saying "The K Desktop Environment" when I hover over the "kde" entry - no mention of "meta". Anyway, I wouldn't have known a "meta package" is safe to remove.)

---

