---
title: "How to remove KDE3?"
date: 2008-06-07
forum: Desktop Environments
---

### Post by JiajiaX2 on 2008-06-07
I'm running Ubuntu (64-bit). Tonight I've install KDE4.1 Beta but it  made my menu in a clutter ! 
Because of having install KDE3.5.9 , so i want to keep KDE4 in my computer and remove KDE3 .
How can i do that? :confused:
 
Thanks!

---

### Post by Anzan on 2008-06-07
Sorry, I don't use KDE at all (after trying it out) but can't you just do this in Synaptic? After all, even if you bork KDE 4 when uninstalling 3, you can always reinstall 4.

---

### Post by JiajiaX2 on 2008-06-07
yeah, Haha.
I'v removed most of the packages of KDE 3  by having typed the following code
```
sudo apt-get --purge remove kdelibs4c2a 
sudo apt-get autoremove
```

after all, thank you Anzan!

---

### Post by tinker88 on 2009-09-03
i too upgraded to KDE4 and wanted to remove KDE3 so i followed the code you stated here and everything ran through fine however when i rebooted the computer it had reverted back to my xubuntu desktop ....now im not sure how to get back to kubuntu ...someone please help me


> **JiajiaX2 said:**
> yeah, Haha.
I'v removed most of the packages of KDE 3  by having typed the following code
```
sudo apt-get --purge remove kdelibs4c2a 
sudo apt-get autoremove
```after all, thank you Anzan!

---

### Post by tinker88 on 2009-09-03
> **tinker88 said:**
> i too upgraded to KDE4 and wanted to remove KDE3 so i followed the code you stated here and everything ran through fine however when i rebooted the computer it had reverted back to my xubuntu desktop ....now im not sure how to get back to kubuntu ...someone please help me


ok i managed to get back to kubuntu kde4 (i forgot to change the session type when logging back in) 

however im still not sure how to enable the 3d cube and i no longer have sound 

can someone please help me?

thanks,
tinker

---

