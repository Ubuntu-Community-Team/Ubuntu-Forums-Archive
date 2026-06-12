---
title: "Automout permissions problems"
date: 2010-10-12
forum: Desktop Environments
---

### Post by Fisher on 2010-10-12
Hello.
I'm using Ubuntu 10.04 LTS with multiseat. It's a single CPU with two users plugged in.
It's working fine but I'm having problems when inserting external media, be it usb drives or even CDs or DVDs.
Only one user can access the external media, he is made the owner of the mount point and the other users cannot even access this mount point.
What can I do to change this? For example, it would be nice to have read permissons for all users when a DVD rom inseted, so anyone can watch a movie and so on.

---

### Post by bobcollard on 2010-10-12
You need to create a group permission for whatever it is.  I've never done it.  You should be able to set it up as root in Users and Groups.

---

### Post by Fisher on 2010-10-12
Both users are administrators and set to the audio and disk groups.
I'm just out of ideas!!!

---

### Post by KoenW on 2010-10-15
It's a bug in gdm and the way it handles sessions with consolekit (and friends) and pam. 
You can patch and compile manually your gdm and consolekit but it should be easier to switch to kdm. 

Look at 
[http://multiseatonlinux.blogspot.com/2010/06/part-1-setting-up-base.html](http://multiseatonlinux.blogspot.com/2010/06/part-1-setting-up-base.html)
if you want to patch your gdm and consolekit.

---

### Post by Fisher on 2010-10-15
I'm already using kdm.
Sincerelly, I'm disappointed! The gnome desktop seens to become worser every new release!!
I once had, in 7.04 a near perfect multiseat. All I needed to do was to configure gdm. Now, I need to use kdm an have all sorts of stupid bugs!
Is it progress?? At one side it is really improving, getting more stable and faster, but at what cost??
Recompile everything is a option, but time is the obstacle! Even now I don't known why does nautilus simply ignores the directories umask!!
Maybe I should switch!! But I dislikes kde, it seems too much like m$ stuff in my opinion.

---

### Post by bobcollard on 2010-10-15
Fisher, try Xubuntu, it is closer to gnome than KDE and has fewer bugs.

---

### Post by Fisher on 2010-10-16
I'll try it, but I've read that Xubuntu is more resource intensive than ubuntu, this should be the opposite...
Think I'll try lubuntu too, anyway I'll put the results here.
I found a way to watch dvds, it's using vlc, somehow it can open the dvd drive even without being other user. Weird but cool!

---

