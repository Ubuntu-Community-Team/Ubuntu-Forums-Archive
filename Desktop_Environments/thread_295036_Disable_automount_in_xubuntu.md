---
title: "Disable automount in xubuntu"
date: 2006-11-07
forum: Desktop Environments
---

### Post by fortran01 on 2006-11-07
Any ideas on how to disable the automounting feature in Xubuntu (e.g. removable devices such as cf/usb flash stick)? I want to always mount removable devices manually. Thanks!

---

### Post by dannyboy79 on 2006-11-07
i know it has something to do with pmount, do a man pmount and see what ya find. this is what I found just looking at it quickly, Some applications like CD burners modify a raw device which must not be
       mounted while the burning process is in progress. To prevent  automatic
       mounting,  pmount  offers a locking mechanism: pmount --lock device pid
       will prevent the pmounting of device until it is unlocked  again  using
       pmount  --unlock  device  pid. The process id pid assigns the lock to a
       particular process; this allows to lock a device by several  processes.

---

### Post by _savior_ on 2006-11-07
It is enabled by default?!

I have a clean Edgy install, but nor the CD, nor the USB automounts. I have to mount the manually, or open them with Thunar (which mounts them).

However, unlike fortran01, I would like them to BE automounted -- which they are not :???:

Could someone pls tell me how to switch automount on?

(dannyboy79: what do you have in your /etc/pmount.allow? Mine is empty)

---

### Post by fortran01 on 2006-11-07
@ _savior_
Mine is empty too. But removables (e.g. USB disk) are auto-mounted for some reason. Btw, my desktop is not really pure Xubuntu. I also installed the meta-packages ubuntu-desktop and kubuntu-desktop. Maybe some automounting scripts were activated. Just a thought.

@ dannyboy79
As for the pmount --lock, I don't have any process to lock the pmounting. I just want to disable that script that automounts hotplugged devices. Thanks anyway.

---

### Post by kerry_s on 2006-11-07
Just add " noauto " in /etc/fstab i use these->
,user,noauto,noatime

The "user" one does not work in edgy, but in dapper it allows the regular user to just click on the drive to mount it. The "noatime" is for no log, suppose to help speed wise.

Ooops, you wanted external not to be mounted.

---

### Post by _savior_ on 2006-11-08
fortran01: maybe you have gnome-volume-manager installed? That DOES do automount; you have to run it before, though (in Xfce session), so maybe this is not fortran01the case with your system.

It would solve my problem, too, but when I tried to install it, it wanted to bring 200 megs of gnome "goodies" with it, including my old friend Nautilus (maybe the whole ubuntu-desktop), so I dropped it. But now I do not know how to set up automount :)

---

### Post by kerry_s on 2006-11-08
> **_savior_ said:**
> 
It would solve my problem, too, but when I tried to install it, it wanted to bring 200 megs of gnome "goodies" with it, including my old friend Nautilus (maybe the whole ubuntu-desktop), so I dropped it. But now I do not know how to set up automount :)

What are you using that it's not automounting? In rox use ivman, thunar automounts to, konqueror also automounts.

---

### Post by dannyboy79 on 2006-11-08
my /etc/pmount.allow is empty as well.

to get a removable device so that it DOESN'T automount, you would just add a fstab entry like what's his name said and ensure you have the option, noauto,user which will not mount it and it'll be able to be mounted by users.

as far as the other guy and his automounting NOT working, I am not sure how to solve that, there are ton's of others dealing with this though, do a search using the forum search feature, something like, automount not working or usb drive or usb flash. good luck

---

### Post by _savior_ on 2006-11-09
> What are you using that it's not automounting? In rox use ivman, thunar automounts to, konqueror also automounts.

XMMS does not, and many other programs do not either. Which is understandable, as it would not be THEIR responsibility to do it.

So an example scenario: I am listening to music. I insert a CD with mp3s on it. I cannot open it from XMMS, I have to clear the desktop->right-click icon->mount (or mount -a in console).

dannyboy79: I DID a search, and not found anything useful, that is why I ask it here :)

I have heard about autofs... anyone has experience with it?

Thanks!

---

### Post by tqiw on 2007-12-22
I know this is an old thread, but a solution is to click "Edit" then "Preferences" in Thunar and then it's on the "Advanced" tab under "Volume Management". The package that enables the auto mounting is thunar-volman I think.

---

