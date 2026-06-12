---
title: "Looks like Mplayer is highjacking my Realmedia"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Omnios on 2005-10-17
After spending hours of different ways of installing Realplayer alien etc with bad links I finely got it going with the bin install. Now I have another issue, my isp home page is called Rogers.yahoo  which is a huge cable cell wireless company in cooperation with Yahoo. Anyways I get multi media news in embeded pop ups on my home page and prefear Realplayer for it.  Mplayer will work but I just dont like it for that. Anyways what is happening is Real player launches in the pop up then a sec later it goes to what looks like the mplayer load and just sits there blank. It looks like mplayer is high jacking it and also in the pop up media preferences after this happenes my preferences show windows media player which it shouldn't and Realplayer is there in the preferences also. 

 I realy don't want to get rid of mplayer but from previos experiences it is a very aggressive program and unless I can config it properly I will need to uninstall it.
 Any help would be appreciated

---

### Post by cytoplasm on 2005-10-17
Take a look at your gnome-vfs.applications file and check for mplayer / realplayer references:

[FONT="Courier New"]$ sudo vim /usr/share/application-registry/gnome-vfs.applications[/FONT]

---

### Post by Omnios on 2005-10-17
Got it working had to check something in XP and when I went back to Ubuntu it started working so not shure if you have to restart X or reboot.

---

