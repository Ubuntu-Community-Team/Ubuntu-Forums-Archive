---
title: "Just upgraded from Warty and now resolution problems"
date: 2005-03-31
forum: Desktop Environments
---

### Post by Diego F. on 2005-03-31
Hi. I've upgraded from Hoary and now I only have a 640x480 resolution available.
In Warty I had nVidia drivers installed and I saw a splash screen that I can't see now.

What can I do? I choose other resolutions in the upgrade and I see them in xorg.conf. The video card is well recognised (nVidia GeForce 5200 Go)

---

### Post by ubuntu_demon on 2005-03-31
[QUOTE=Diego F.]Hi. I've upgraded from Hoary and now I only have a 640x480 resolution available.
In Warty I had nVidia drivers installed and I saw a splash screen that I can't see now.

What can I do? I choose other resolutions in the upgrade and I see them in xorg.conf. The video card is well recognised (nVidia GeForce 5200 Go)[/QUOTE]
 sudo dpkg-reconfigure xserver-xorg

---

### Post by Diego F. on 2005-04-01
I could not start X after doing that. I'm not sure about configuring it.   :-(

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=Diego F.]I could not start X after doing that. I'm not sure about configuring it.   :-([/QUOTE]
 first do :

sudo apt-get update
sudo apt-get dist-upgrade

then try sudo dkpg-reconfigure xserver-xorg again because sometimes it's just a bug. I experienced a resolution problem myself two days ago.

see : [http://www.ubuntuforums.org/showthread.php?t=23013](http://www.ubuntuforums.org/showthread.php?t=23013)

---

### Post by Diego F. on 2005-04-01
Well, it's a bit better now. I ran sudo dkpg-reconfigure xserver-xorg again, but now I've chosen nv instead of nvidia. I removed nvidia in Synaptics and when tried to install again it wasn't available.

Now I'm with 1024x768 and lower ones available. I'll keep trying until 1280x800 that I had in Warty.

---

### Post by Diego F. on 2005-04-01
I don't know why, but it's solved :-)

I put 1280x800 in every depth in xorg.conf and now I can select it, but also the others that follow 1280x800, although they were there before and I couldn't select them  :???: 

Now I have to work on the fonts (they are too thin) and with the nVidia driver (I use nv)

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=Diego F.]I don't know why, but it's solved :-)

I put 1280x800 in every depth in xorg.conf and now I can select it, but also the others that follow 1280x800, although they were there before and I couldn't select them  :???: 

Now I have to work on the fonts (they are too thin) and with the nVidia driver (I use nv)[/QUOTE]
 good

PS I thought I had just suggested editting your xorg.conf after your previous post but I apparently closed my window on accident :)

---

