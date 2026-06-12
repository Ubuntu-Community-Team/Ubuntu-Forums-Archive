---
title: "Natty Narwhal + Compiz Settings Tweak = Disappearing Menu Bars"
date: 2011-06-12
forum: Desktop Environments
---

### Post by cipherchaser on 2011-06-12
I just upgraded my system to Natty Narwhal and was messing with Compiz Config Settings Manager to see if I could move the new application display bar around.  Unfortunately, I somehow disabled a bunch of things because upon closing Compiz, all I could see was my desktop.  No menu bars.  I tried to open a terminal, but my keyboard shortcuts aren't working either.

I WOULD just reinstall the system, but I'm using an EEEPC that doesn't have a CD drive, and I can't make a bootable flash drive.

How do I get my menu bars and general Ubuntu functionality back?

---

### Post by ivanovnegro on 2011-06-12
Try to go to Ubuntu Classic from the login prompt after you clicked on your user name and then try in a terminal:

```
unity --reset
```

---

### Post by cipherchaser on 2011-06-12
When I typed that in, I got this:

> WARNING: no DISPLAY variable set, setting it to :0
Traceback (most recent call last):
   File "/usr/bin/unity", line 198, in <module>
       reset_unity_compiz_profile ()
   File "/usr/bin/unity", line 74, in reset_unity_compiz_profile
       except (GError, AttributeError), e:
NameError: global name 'GError' is not definedWhen I logged in normally, my menu bars were still gone.

---

### Post by wildmanne39 on 2011-06-12
> **cipherchaser said:**
> I just upgraded my system to Natty Narwhal and was messing with Compiz Config Settings Manager to see if I could move the new application display bar around.  Unfortunately, I somehow disabled a bunch of things because upon closing Compiz, all I could see was my desktop.  No menu bars.  I tried to open a terminal, but my keyboard shortcuts aren't working either.

I WOULD just reinstall the system, but I'm using an EEEPC that doesn't have a CD drive, and I can't make a bootable flash drive.

How do I get my menu bars and general Ubuntu functionality back?
Hi, after you reset unity you can use link to get the cube and other effects working in natty.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed.

---

### Post by cipherchaser on 2011-06-12
> **wildmanne39 said:**
> Hi, after you reset unity you can use link to get the cube and other effects working in natty.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed.
Thanks for the link!  Once I get the reset to work I'll check it out.  :)

---

