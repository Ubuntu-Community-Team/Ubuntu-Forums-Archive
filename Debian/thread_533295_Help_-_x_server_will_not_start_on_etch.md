---
title: "Help - x server will not start on etch"
date: 2007-08-23
forum: Debian
---

### Post by seattle vic on 2007-08-23
I'm fairly new at this, but not a total rookie.  Anyway, I've been using Ubuntu for about a month now, and decided to bring up Debian just for the heck of it.  They're both on the same machine so see the same hardware.  Ubuntu boots up just fine with Gnome and everything, but Debian ends up with:

(EE) No devices detected.

Fatal server error:
no screens found

I'm running an nvidia 8600 GT, and the inputs on the xorg.conf files are similar.

I launched a help message on the debian forum, but only got one response, so figured I'd give it a shot here.  That response was:

=====================
You need to link the proprietary NVidia driver.

1. Install headers for your kernel:
apt-get install linux-headers-$(uname -r)

2. Install the libraries that don't need relinking:
apt-get install nvidia-kernel-common
apt-get install nvidia-glx

3. Install the "source" (includes binary blobs):
apt-get install nvidia-kernel-source

4. Read /usr/share/doc/nvidia-kernel-source/README.Debian for more information on what to do next

5. When everything is running, you might want a tool to tweak things:
apt-get install nvidia-settings
==========================
I was able to install the headers and nvidia-kernel-common, but apt-get couldn't find nvidia-glx or nvidia-kernel-source, though it did say there were dependencies for them.

I'd probably just forget about debian, but it's a challenge, and should be a learning experience for me.  I've also attached the  xorg-conf files for both ubuntu and debian.  Both of the log files were over the 19.5 kbyte limit for attachments.  (a way to overcome that??)

Thanks in advance...

---

### Post by Pancetilla on 2007-08-24
No Nvidia in official repositories, Debian is very careful with that....Look elsewhere ([debian non-free]("http://packages.debian.org/cgi-bin/search_packages.pl?keywords=nvidia&searchon=names&subword=1&version=stable&release=non-free")) or download the propietary drivers from Nvidia,install and then change "nv" in xorg (just after "driver") and write "nvidia". This should work.


You've got:

"nVidia Corporation NVIDIA Default Card"
	Driver		"nv"                                 
	BusID		"PCI:1:0:0"
EndSection

and I think it should read:

"nVidia Corporation NVIDIA Default Card"
	Driver		"nvidia"                                 
	BusID		"PCI:1:0:0"
EndSection

---

### Post by seattle vic on 2007-08-24
Thanks for the input.  I did all that, found the not-free repository and added to the sources.lst file and apt-get found it.  changed nv to nvidia, etc and on next boot up it "did" get to the xserver as far as I could tell, but the screen went blank, so I assume there's still an issue with the video card.  I was able to edit the xorg.conf file again from my adjoining ubuntu os on another partition to lower the resolution, but no joy.

So, that's progress, but I'm still stuck.  Good thing I'm off work nursing a bad knee, because I have all day to figure this out.

Vic

---

### Post by Pancetilla on 2007-08-24
¿Does xorg fail or it is just a blank screen?

It may be a monitor Hz issue....

another issue could be the driver version. You've got a new card and, acording to Debian:

Package nvidia-glx
stable (x11): NVIDIA binary XFree86 4.x driver [non-free] 
1.0.8776-4: amd64 i386 

so it is nvidia driver 1.0.8776-4. Current nvidia driver version from nvidia homepage is  100.14.11, try with the newer one just in case

---

### Post by seattle vic on 2007-08-24
OK, I'll try and load it.  I don't know how to check the driver version on my system, but I'm sure I can figure that out.

Thanks...

---

### Post by seattle vic on 2007-08-25
Tried the new driver, and used the nvidia installer.  It didn't crash with an error message, so it recognized the driver, but I got a blank screen.

Maybe I need to start over and do the upgrade sequence with this new driver?  This seems more complicated than it should be.

Vic

---

