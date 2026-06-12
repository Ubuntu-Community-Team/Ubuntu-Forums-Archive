---
title: "GNOME session - system freezes"
date: 2006-09-17
forum: Desktop Environments
---

### Post by bastiegast on 2006-09-17
Yesterday a friend of mine gave me his old computer. I whiped out the hard drive and did a fresh ubuntu installation. Everything went fine, no problems during installation and after i installed codecs and firefox plugins with no problems. 
Until i opened my case to blow the dust out of the fans. After i did that i assambled my pc again, booted up, logged in started firefox and my system freezes ](*,) . Totally... no ctrl-alt-backspace or ctrl-alt-F1, just complete freeze. So i reboot my computer again, log in and start synaptic, again a total freeze. After a few reboots i noticed the freezes seem to occur  with firefox, synaptic but not with the terminal for example.
I have now logged in into a x-tterm safe mode session, from here i can start synaptic and firefox with no problems.
So: first everything works fine, next total system freezes. The only things i can remember doing between was trying to get XGL working(no succes, using geforce 2 ti with nvidia-glx-legacy) and opening my computer case.

---

### Post by mistajon on 2006-09-17
Yes I have upgraded from breazy to dapper and freezes with Firefox only.  I dont use it now.  I use vmware with winxp and use firefox in that instead.  Can someone please investigate why this freeze is occuring? I can move the mouse but not click anything and the keyboard does not respond.  I have to cold reboot.

---

### Post by pay on 2006-09-17
Yeah firefox was freezing with me also and it kicked me out of my gnome session and occasionaly completly froze...

---

### Post by bastiegast on 2006-09-17
> **mistajon said:**
> Yes I have upgraded from breazy to dapper and freezes with Firefox only.  I dont use it now.  I use vmware with winxp and use firefox in that instead.  Can someone please investigate why this freeze is occuring? I can move the mouse but not click anything and the keyboard does not respond.  I have to cold reboot.

Looks similair to my problem, i too can still use my mouse

> **pay said:**
> Yeah firefox was freezing with me also and it kicked me out of my gnome session and occasionaly completly froze...

Actually for me it just worked, but then something happened and suddenly i got crashes.

---

### Post by bastiegast on 2006-09-17
UPDATE: 
Problem fixed :cool: :D 
I commented out the
    Option "RenderAccel" "true"
from my xorg.conf, somehow this was causing the freezes, must say i feel kinda proud having figured this out.:biggrin:

My video card is a GeForce 2 titanium, i posted this in case anyone else has similair problems.

---

