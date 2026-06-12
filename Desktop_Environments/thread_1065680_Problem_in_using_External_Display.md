---
title: "Problem in using External Display"
date: 2009-02-10
forum: Desktop Environments
---

### Post by qtzaman on 2009-02-10
Hello Everyone, very recently I have migrated from Win XP Pro to Ubuntu 8.04 LTS. Everything seems to be working fine, except, I can't use external Display. I'm using HP nc6230 notebook which has ATI Mobility Radeon x300 VGA. Can anyone help me that how can I enable an External Display such as a Multimedia Projector.

---

### Post by kimberlite on 2009-02-10
You can try "grandr" panel applet to calibrate the resolution of different display devices. Otherwise when you go to -> setting -> screen resolution, there you will find some options how to set external devices. However grandr is more useful, when you want to control which display should be on/off.
Note: sometime you need to reboot or at least restart X (CTRL+BACKSPACE) to be able to use an external display device.
PS. Sorry, I did not realized that you are runing KDE. The grandr app is for Gnome environment... However you can try to use it, although you will have to install GTK libraries with it. Other option is xrandr. It has similar functionalities, but no GUI.

---

### Post by spazz135 on 2009-02-10
i would do the same thing but i would maybe see if another monitor works and if its just not a driver or something

---

### Post by damnhappy on 2009-02-24
I give lots of presentations, and this has always been a sticking point for me, but I installed grandr and it works like a charm! 
Thanks  so much for your help. 

ps 

I installed i810 a while back too- this may or may not be neccessary, don't know. 

Thanks!

---

