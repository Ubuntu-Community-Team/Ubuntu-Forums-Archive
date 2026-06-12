---
title: "No DVI with my nvidia card."
date: 2005-05-03
forum: Desktop Environments
---

### Post by basse1989 on 2005-05-03
Hello

I have a problem, when I use the "nvidia" driver my geforce 6600 wont work with DVI in xorg. It sends no signal, but it works with VGA.  :???: When I used a Radeon 9600 DVI worked but now with my new card I have to use VGA with my TFT screen. DVI works with the "nv" driver (for some reason X shows up in 640x480) but I want 3D acc.

Someone please help me.

EDIT: A friend of mine has the exact same card and DVI works for him.

---

### Post by shakin on 2005-05-03
I bet your DVI is considered the secondary device. If you configure dual screens that one will be your second screen.

You might be able to switch them using some NVidia control panel or by changing the BusID in /etc/X11/xorg.conf

eg.
BusID		"PCI:0:2:0"

---

### Post by basse1989 on 2005-05-03
Thanks for your reply.
First, I have only one screen, a TFT one which have both a DVI and VGA interface.
Second, I disconnect the VGA cable before I restart X but with no luck. :(

DVI works fine before X starts.

---

### Post by hobbestec on 2005-05-03
You might need to add the ConnectedMonitor string to your video card config in xorg.conf

Something like:

Option "ConnectedMonitor" "DFP"

You can read the full nvidia instructions here: [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7174/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7174/README.txt)

---

### Post by basse1989 on 2005-05-03
Thanks a lot!
Now it works, I'm finally back to DVI! :)

---

