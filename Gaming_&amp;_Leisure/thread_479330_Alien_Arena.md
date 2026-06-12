---
title: "Alien Arena"
date: 2007-06-20
forum: Gaming &amp; Leisure
---

### Post by phizikal on 2007-06-20
Okay, I've been looking at screenshots of this game. I also heard it runs extreme fast on weak machines. I've been googling for articles on how to install it, and still don't find any.

Can anyone give me details on how to download it and install it thought terminal, incase you wanted to know. I use dapper.

Please and thank yous.

---

### Post by derjames on 2007-06-20
though I haven't inatalled yet... I was reading some stuff from the alien arena forum... perhaps is a good place to start

[http://corent.proboards42.com/index.cgi?board=aatech](http://corent.proboards42.com/index.cgi?board=aatech)

---

### Post by RomeReactor on 2007-06-20
Hi. If you already have your video card setup for 3D acceleration, then you can get a .deb file for Alien Arena [here]("http://www.getdeb.net/release.php?id=395"). Once the download finishes, just double-click on the file to install.

---

### Post by phizikal on 2007-06-20
Okay, this may be stupid.
How can I set-up my video card for 3D acceleration?

=/

---

### Post by RomeReactor on 2007-06-20
Open a terminal (Applications-->Accessories-->Terminal) and enter:
```
glxinfo | grep rendering
```
The response should say **Yes**. If it does, then you already have acceleration (direct rendering) enabled.

---

### Post by phizikal on 2007-06-20
it says no.

---

### Post by RomeReactor on 2007-06-20
Do you have a nVidia, ATI, or integrated (intel, savage) video card?

---

### Post by phizikal on 2007-06-20
nvidia.

---

### Post by RomeReactor on 2007-06-20
Do you know what model? If not, or you are unsure, try this from the terminal:
```
sudo lshw -class display
```

---

### Post by phizikal on 2007-06-20
description: VGA compatible controller
       product: NV6 [Vanta/Vanta LT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@01:00.0
       version: 15
       size: 32MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: driver=nvidia

---

### Post by phizikal on 2007-06-20
I am hoping that helps?

---

### Post by phizikal on 2007-06-20
OK, I ran the game. And it's lagging badly, I def need booosta!

---

### Post by RomeReactor on 2007-06-20
Your video card has 32 mb of memory, which I would say is little to run the game; but you won't know for certain until you try, so let's try getting that acceleration going: first, backup your **xorg.conf**:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
then:
```
sudo nvidia-glx-config enable
```
after that, run
```
glxinfo | grep rendering
```
again to see if you have rendering now.

---

### Post by phizikal on 2007-06-20
Second command doesn't work.

```

root@admin-desktop:/home/admin# sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
root@admin-desktop:/home/admin# sudo nvidia-glx-config enable
sudo: nvidia-glx-config: command not found

```

---

### Post by RomeReactor on 2007-06-20
That's odd, unless you're not using the **nvidia-glx-legacy** drivers; do a search for nvidia on Synaptic and see which one is installed.

---

### Post by phizikal on 2007-06-20
it's nvidia-glx-legacy.

=)

---

### Post by RomeReactor on 2007-06-20
Hmmm... try:
```
sudo nvidia-xconfig
```

I think you must have **nvidia-kernel-common** installed as well.

---

### Post by phizikal on 2007-06-20
No, got a command not found. =/

I wonder why this is getting so complicated. :(

---

### Post by Primus on 2007-06-20
The Vanta is a very very old card (Riva TNT2 based) - so don't expect too much from it. You can pick up GeForce 6 cards now for about £20 ($30-$40).

---

### Post by phizikal on 2007-06-20
wait h/o.. 

all my nvidia packages wasn't installed. im installed them

this is what i got...


```

root@admin-desktop:/home/admin# sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


```

---

### Post by RomeReactor on 2007-06-20
**EDIT**: I just read your last post: what packages did you install? Check if you have rendering now:
```
glxinfo | grep rendering
```
If you do, then your card is ready to play the game (just don't expect great performance from it). If you still don't have rendering, then the last thing I can think of right now is to reconfigure your display; however, this can break your xorg.conf, resulting in you logging back in to a terminal (black screen with white text, no graphical environment), though I don't think there's too great a chance of that. If you want to go ahead and do this, then:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If X does break, you have to run this command to restore it:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and
```
sudo reboot
```
If this doesn't enable rendering, it may be a good idea to search the [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=138") section of these forums for help. Sorry if this doesn't work, I'm out of ideas at the moment.

---

