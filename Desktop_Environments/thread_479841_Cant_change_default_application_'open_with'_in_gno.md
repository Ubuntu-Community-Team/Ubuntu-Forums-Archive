---
title: "Cant change default application /'open with' in gnome"
date: 2007-06-20
forum: Desktop Environments
---

### Post by blu30n3 on 2007-06-20
hi im using gnome and when i try to change my default application for like mp3's or anything by using **right click file > properties > open with tab > and select application**, it dosnt allow me to change the applicaiton to open with. ive been having this issue for some time now, last thing i did to try and resolve was **sudo dpkg-reconfigure -a** to reconfigure the entire system same issue, and tried removing movie player (mplayer) because this is now the default app to open most media files, but that didnt work either. issue is persistent with all files formats................. also cant remove applications from openwith list only add.
                  Any one have any suggestions?

---

### Post by rax_m on 2007-06-21
That should work ( it does for me!) .. 

Could you please be more clear as to what you mean by "doesn't allow you to" .. perhaps a screenshot?

rax_m

---

### Post by trogo on 2007-06-21
I have the same issue too!!
There's no need of any screenshot: just right click on any file on nautilus and then go to properties-> open with
The menu is there but you are not allowed to change or delete applications to open the file... you can just add new applications to the list!!!
I installed ubuntu 7.04 feisty fawn 32bit yesterday and it was working, then i added a new session to use beryl with xgl and today i noticed this issue! I don't know if it is related to beryl! I also installed many video players (mplayer, xine-ui and vlc) but nautilus forces me to use totem as default!!

I found some kind of solution here: (it's an italian blog, however the code is understandable for all)
[http://paper0k.wordpress.com/2006/11/13/gnome-apri-con-non-mi-permette-di-selezionare-nulla/](http://paper0k.wordpress.com/2006/11/13/gnome-apri-con-non-mi-permette-di-selezionare-nulla/)

I'd like to unlock nautilus!!

Help!

---

### Post by trogo on 2007-06-21
Ok now you can ban me!

As ever, after half an hour of googling i did not find any solution. However, a minute after my post on the forum, i found it!

[http://ubuntuforums.org/showthread.php?t=262487](http://ubuntuforums.org/showthread.php?t=262487)

Thank you all! blu30n3 check if it works for you, it does for me!

---

### Post by rax_m on 2007-06-21
glad it's solved .. sorry i haven't seen that issue before. 

I've heard issues where running GUI applications as root using "sudo" instead of "gksudo" causes file ownership issues.. just thought I'd mention it in case someone has been doing this.

---

### Post by blu30n3 on 2007-06-24
ya i tried that and i beleive i had tried that before too.. mine still isnt working, not sure why, if anyone else has any solutions id love to hear them... thnx though, i swear that fix should have worked but eh, gonna have to reinstall ubuntu sometime .. lol...

---

