---
title: "Thrashed Display?"
date: 2005-12-15
forum: Desktop Environments
---

### Post by wynterbourne on 2005-12-15
So, while I have been using ubunutu almost exclusively this week so far, I have noticed one small glitch on my Sony Vaio. 

Occastionally, the display goes completely insane. I have to reboot, in order for it to return to normal. I did manage to get a screen shot that will be attached (if I can do that) for anyone interested.

I believe it's my video card, but I'm unsure how to fix this or go about looking into it. Any help would MUCH be appreciated! Thanks!

---

### Post by RAOF on 2005-12-15
I've had that (or a similar) problem with the "nv" free nvidia drivers.  Do you know what sort of graphics hardware your Vaio has?

Also, rather than rebooting, I found that changing the resolution was also a temporary fix.  You might be able to try that.

---

### Post by wynterbourne on 2005-12-16
I have noticed I can reset the display for a temp fix. Looking at my information in Windows XP, I'm thinking its a 

NVIDIA GeForce Go 6400. Sound right?

---

### Post by jrb114 on 2005-12-21
I've had that display issue to. (on Breezy).

I've got a new Sony Vaio VGN-FS315S with a Geforce 6400 Go. Originally the default nvidia drivers worked, but I'm trying to sort out a couple other problems too, so I compiled a new kernel, and switched to nv. Every so often the screen goes completely crazy (but if I click and drag with the mouse to select text I can often still read it). Ctrl+Alt+Backspace to restart X usually works. though. 

One odd thing - I've tried to reinstall the nvidia drivers for the new kernel, so I followed the how to [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=howto+nvidia](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=howto+nvidia)
to compile the driver, but for some reason (I've tried removing all nvidia references in synaptic) it won't start X after apparently compiling fine. This could be a bit issue (especially with nv trashing the screen from time to time).

So, while I'm on the topic, things about the Vaio I've got problems with, and if any kind folks could help me out, I'll be happy to oblige.

Suspend to ram / or to disk (hibernate). Neither of these worked out of the box. I've tried suspend2 and it seems to "hibernate" pretty well now, except when it reaches the end of it's writing cycle it doesn't turn off - I have to hold down the power button. On rebooting it resumes fine.

Hot reboot - originally during set up the machine just locked up, and trying to do a reboot always failed. Others seem to had this problem, passing "reboot=h" to the kernel on boot fixed this. I don't know whether this is a similar problem to hanging at the end of writing the memory to disk in suspend2 (above).

WPA: I'm running wpa_supplicant to connect to WPA network using ipw drivers. Weirdly, on boot, the interface connects (or seems to), syncs the time with utp(??).ubuntulinux &etc but when X starts and I try to run firefox etc, the interface is down. If I run "dhclient eth0" (my wifi is eth0, ethernet socket eth1, I don't understand) everything is fine.

My /etc/network/interfaces:

============================

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
         script grep
         map eth0

iface eth1 inet dhcp

auto eth0
iface eth0 inet dhcp
wireless-essid <my essid>

=============================

To correct this problem, like I said, I can do a "dhclient eth0" or, from the networking GUI, simply "Activate" the wireless and it's all good.

Other goodies with the Vaio were working - before I tried to get suspend2 to work, I had the FN keys working letting me change the brightness and volume. I'm guessing that they'll work again when I get round to recompiling the module for the new kernel. But then again, I thought nvidia would work too.

So, all in all, I'm a bit stuck. I'm learning loads - good job I've good two desktops successfully running under Hoary and Breezy, need all the experience and help I can get. If anyone out there has ideas! Please help.

J

---

### Post by andreao on 2006-01-02
Hi!
I 've yet bought a VAIO FS315M with GeForce GO 6400 and I have all the problems you have mentioned in the post.
I've tried both nv and nvidia drivers, however with nv I can set 1280x800 resolution (and it is veeeery nice!) but sometimes displays -as you've said- goes insane.
Nvidia driver seems to work well, but can only accept a resolution of 1280x768 (it's orrible!)..
Is there anybody that can use GeForce GO 6400 work well with kubuntu?
Thanks!

---

### Post by jdk_ on 2006-04-06
Hi, 

I have a FS315M and had this problem too, for me it disappeared when I finally got the nvidia driver from nvidia.com working. The version that made everything work for me was NVIDIA-Linux-x86-1.0-8174-pkg1.run. I had the problem of not being able to use 1280x800 resolution, but 1280x768, with a previous one, it was 7???.

Hope you get the problem solved soon, I would definitely recommend giving 8174 or a later one a try.

Finally, nice to find more people with FS315M, it is working very well for me even when I haven't been so keen on setting up everything that is likely to work. Just wondering... do you have scrolling with the touchpad? (Sorry for the off-topic, I just couldn't resist the temptation ;) )

---

