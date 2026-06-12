---
title: "XFCE problems (apps work as root, don't work when logged as normal user)"
date: 2006-08-22
forum: Desktop Environments
---

### Post by dolny on 2006-08-22
I tried xubuntu-desktop packages, sources, svn, official installer, but everythime after installation of xfce, some apps work with normal permissions and some of them, like xfmedia or mousepad work only with 'sudo'. Does someone know why? 

```
trainchaser@acer:~$ xfmedia
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(xfmedia:30581): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `ExoEllipsizedLabel'

(xfmedia:30581): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `ExoEllipsizedLabel'
Segmentation fault
trainchaser@acer:~$ sudo xfmedia

** (xfmedia:30604): WARNING **: Failed to open a connection to the D-BUS session bus.  Please ensure that the session bus is running. (4: No reply within specified time)

** (xfmedia:30604): WARNING **: Failed to open a connection to the D-BUS session bus.  Please ensure that the session bus is running. (4: No reply within specified time)
trainchaser@acer:~$             
```

BTW. I'm a total noob when it comes to XFCE, I just installed it on my laptop, how do I activate compiz? (I chose it to be integrated into XFCE when I installed it using the GUI installer from xfce.org)

---

### Post by dolny on 2006-08-22
Hmmm... and it also doesn't remember my settings. I changed the wallpaper, icons and stuff, logged out, then logged in and XFCE looked like it did right after the installation - the default wallpaper etc. Can anybody help?

o_O What the... After I launch xfce-setting-show by using sudo, the icons, wallpaper etc. change to the ones I chose (not the default ones)

Seems like some weird permission problem. I would really appreciate your help guys.

---

### Post by dabear on 2006-08-22
Hm.. having problems with xfce here too..
Are you able to let xfce manage your desktop? It's just black here, even if I enable it in the Desktop Preferences

edit; and there seems to be something strange going on with the text in settings manager:

---

### Post by K.Mandla on 2006-08-22
I haven't noticed anything like that, but I converted my Xubuntu into a funky Edgy-XGL hybrid (EXGLubuntu?), so it might be my machine. 

I do know that I can't let XFCE manage the desktop without clicking that option each time I reboot, but it's a nonissue for me, and I had blamed it on Edgy.

---

### Post by dolny on 2006-08-23
Any other opinions? Please? ;>

---

### Post by lepre on 2006-09-12
i'm having a similar issue after upgrading from xfce 4.4beta2 to 4.4rc1.

if i try to play an mp3 with xfmedia it tells me that i don't have permissions. if i run it as sudo it works. but it was working without any change in the permissions before i upgraded the enviroment.

:(

---

### Post by om.prakash on 2008-03-06
> **dolny said:**
> Hmmm... and it also doesn't remember my settings. I changed the wallpaper, icons and stuff, logged out, then logged in and XFCE looked like it did right after the installation - the default wallpaper etc. Can anybody help?

o_O What the... After I launch xfce-setting-show by using sudo, the icons, wallpaper etc. change to the ones I chose (not the default ones)

Seems like some weird permission problem. I would really appreciate your help guys.

[B]I also need to do that like changing the default wallpaper, icons and default theme.
Please could you tell me how did you do that.
Thanks in advance.[/B]

---

