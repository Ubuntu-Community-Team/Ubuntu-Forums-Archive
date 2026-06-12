---
title: "How To Get Drive Icons on Desktop ???"
date: 2012-07-28
forum: Desktop Environments
---

### Post by ohnonot on 2012-07-28
hello everyone,
on my xubuntu 11.10 installation i have been trying out other desktop/file-managers but none of them (not even nautilus which i installed only to see how it handles the desktop) displays icons for drives and devices on my desktop. only xfdesktop does that.
i'm talking about icons for external hd's, usb devices and cd drive and sometimes also "file system" or "computer".
:confused:

i think i'm missing something obvious here, because all file managers i use display these icons on the left hand pane and afaik they all get auto-mounted.

any suggestions?
thanks in advance.

------------------------------------------------------------------
further explanation (you don't have to read this):
 
basically nothing wrong with xfdesktop but i can't get it to open folders/drives with a file manager of my choice. it always uses thunar, even if i have symbolic links named "thunar" linking to my favorite file manager. at the moment i like pcmanfm and spacefm.

also, it seems quite a few people confuse "displaying desktop icons" with "displaying drives and removable devices on the desktop" - i just want to point out that i'm talking about the latter.

---

### Post by Laiquendi on 2012-07-28
You can change it using Ubuntu Tweak :)

---

### Post by ohnonot on 2012-07-30
> **Laiquendi said:**
> You can change it using Ubuntu Tweak :)it seems ubuntu tweak has no effect on my system - it seems to read information but nothing changes (i tried the janitor and the above mentioned desktop icons).
anyway i'm pretty sure ubuntu tweak is mostly for gnome desktop, and i'm using xubuntu with xfce, and i'm trying to replace one or two components of the xfce desktop environment (xfdesktop and/or thunar) with others (spacefm, pcmanfm...). i don't think this is a job for a program like ubuntu tweak, but hey, i'm open to every kind of solution.
thanks.

---

### Post by brainwash on 2012-07-30
> **ohnonot said:**
> hello everyone,
on my xubuntu 11.10 installation i have been trying out other desktop/file-managers but none of them **(not even nautilus which i installed only to see how it handles the desktop)** displays icons for drives and devices on my desktop. only xfdesktop does that.
Nautilus is able to display _mounted_ volumes. Simply run this command to enable the option:
```
$ gsettings set org.gnome.nautilus.desktop volumes-visible true
```

Another idea would be to remove Thunar and keep xfdesktop as desktop manager. However, you won't be able to do some tasks like creating new folders on your desktop or viewing file/folder properties.

---

### Post by ohnonot on 2012-08-06
yes, when i use nautilus for managing the desktop i can change that setting as brainwash described or with ubuntu tweak - i guess it's the same thing, one with command line, the other with gui.

however, the problem persists: both nautilus and xfdesktop don't give me a choice which file manager gets started when clicking drives/folders on the desktop (although, i read somewhere that this is possible via d-bus).
or, on the other hand, pcmanfm/spacefm don't give me drive icons, i don't know is it by design or am i missing sth.

thanks for posting. more help?

---

### Post by ohnonot on 2012-09-01
> **brainwash said:**
> Another idea would be to remove Thunar and keep xfdesktop as desktop manager. However, you won't be able to do some tasks like creating new folders on your desktop or viewing file/folder properties.- have you actually tried this? i'm a bit afraid to wreck my system with something like this...
:-k

---

