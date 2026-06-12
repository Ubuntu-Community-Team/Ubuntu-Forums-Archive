---
title: "disable auto mounting of USB drives &amp; File Browser"
date: 2009-08-23
forum: Desktop Environments
---

### Post by George Heine on 2009-08-23
Just installed Ubuntu 9.04, and trying to do some configuration.
Found this item on the forum from October 2006:

**"Re: How to disable hardware detection for a CD drive**

To disable automatic mount of cd/dvds in Gnome, you should go to:
System->Preferences->Removable Drives and Media..."

<><><><><><>
Actually I want to disable automatic mounts of -any- removable media,
-and- also disable the Gnome popup of the 'File Browser' screen.

There doesn't seem to be a "Removable Drives and Media" in System>Preferences
anymore.  So, how?

thank you for any help you can give !

George Heine

---

### Post by aysiu on 2009-08-24
Yeah, it moved.

Places > Home > Edit > Preferences > Media

---

### Post by George Heine on 2009-08-25
Thanks, but am still lost.
Am away from the Ubuntu box at the moment, but from memory -
My "Places" menu does not have an entry for "Home".
There is an entry for "Home Directory", but it just opens a File Browser to  /home/<username>.
 
Is there a way to disable automounting/file browser by either 
 
(1) editing one of gnome's configuration files (there seem to be dozens of them);
(2) avoiding gnome altogether and just editing the system config files (for example,
put lines such as "/dev/sdb1....noauto." in  /etc/fstab.).  Has anyone tried this?
What about File Browser?  Personally, I never use it and would be happy to get rid
of it.   
 
thanks again for your help -

---

### Post by aysiu on 2009-08-25
> **George Heine said:**
> Thanks, but am still lost.
Am away from the Ubuntu box at the moment, but from memory -
My "Places" menu does not have an entry for "Home".
There is an entry for "Home Directory", but it just opens a File Browser to  /home/<username>. That's exactly what you want.

And when the file browser opens, click on Edit > Preferences and then navigate to the Media tab.

---

### Post by cong06 on 2010-07-30
in Lucid, uncheck "browse media when inserted"

or run:
```

gconftool --set /apps/nautilus/preferences/media_automount_open --type bool "false"

```

There is also:
```

gconftool --set /apps/nautilus/preferences/media_automount --type bool "false"

```
Which I think skips auto-mount all together.

---

### Post by George Heine on 2010-11-28
cong06 -

Checked this old thread while preparing to install a new OS, and found your response.
Both of your command-line ideas work perfectly -- was able to turn on and off both automatic
browsing of newly mounted systems, and turn off automount altogether. 

Clearly, I need to learn about gconftool.
Thanks !  

Marked the thread as solved.

---

