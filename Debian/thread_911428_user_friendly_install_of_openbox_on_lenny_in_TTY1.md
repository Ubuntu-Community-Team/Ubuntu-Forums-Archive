---
title: "user friendly install of openbox on lenny in TTY1"
date: 2008-09-05
forum: Debian
---

### Post by di@bl@l on 2008-09-05
Hi guys,

I'm from the french community ubuntu-fr.

I come here to present you a script I collaborate on.

This script allow you to install openbox fully configured on a debian lenny standard install.

By downloading, chmoding and executing this script, you can :
- choose the way to boot (GDM / autologin (w/o pass) / startx (with pass))
- choose between two panels : pypanel and fbpanel
- choose between two file managers : thunar and pcmanfm (latest version in debian with tabs...)
- install the following items : Oo, multimedia stuff, flash, wicd, classic apps (evince / iceweasel / brasero / gpicview) , pidgin, emesene, gimp, codecs, MS fonts, Java, gnome office, gnome games.

Furthermore, these shortcuts are available :

> right clic : openbox menu
Middle clic : desktop browser

ALT + F2 : applications launcher Gmrun
CTRL + ALT + directions : to change the desktop

Win + d : show desktop
Win + e : file manager Thunar or PCman FM
Win + w : web browser Iceweasel
Win + n : notepad Leafpad
Win + p : xfce4-taskmanager
Win + s : Synaptic
Win + t : Terminal
Win + a : music player Audacious
Win + v : media player VLC

Prt Scr : screenshot

ALT + w : reduce volume
ALT + x : raise volume
ALT + c : mute

This script has bee tested a lot of time and work perfectly.

I let you discover it by yourselves at the following page :
[bee script]("http://bee.kowazy.be/dist/lenny/bee")

The french thread is here :
[http://forum.ubuntu-fr.org/viewtopic.php?id=248558]("http://forum.ubuntu-fr.org/viewtopic.php?id=248558")

To install, download the netinstall of lenny beta 2 here :
[debian lenny iso]("http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-netinst.iso")

Install it with the standard system (i.e. minimum)

Reboot, log as root, and write the following commands :
```
wget http://bee.kowazy.be/dist/lenny/bee
chmod +x bee
./bee -i
```

Just one preview of what you'll get :

[[img]http://pix.nofrag.com/1/3/f/cbc541e120080a1c436d55b211914.png[/img]](http://pix.nofrag.com/1/3/f/cbc541e120080a1c436d55b211914.html)

Good luck, don't hesitate to try it on virtualbox before.

i'm here for the questions.

---

### Post by Rocket2DMn on 2008-09-06
Moved to the Debian forum area.

---

### Post by di@bl@l on 2008-09-06
> **Rocket2DMn said:**
> Moved to the Debian forum area.

Thanks.

---

### Post by imagecko on 2008-09-10
Intresting.
I think i will try this out some day.

---

