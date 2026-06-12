---
title: "ubuntu freezes after login"
date: 2006-04-24
forum: Desktop Environments
---

### Post by broy on 2006-04-24
I have downloaded the x86 version of Ubuntu 5.10. I have installed it about three times and I always have the same problem. As soon as I login the music will play and then it will stop and then play a little more almost like a cd skipping and then it would freeze completely. I have burned the DVD at 4x in an attempt to fix the cd but I don't think that's the problem since installation went smoothly. I am new to linux so if anyone can help me I would really appreciate it. I also should mention that I have ubuntu dual booted with windows xp pro.

When it is loading it says:
deterred execution scheduler  [fail]

My system is:
AMD Athlon 64 3000+
MSI K8-Neo Motherboard
256mb X600 pro pci-x
Western Digital 200gb SATA hard drive
1Gb DDR 400

---

### Post by Kethinov on 2006-04-24
Post the contents of /var/log/Xorg.0.log

---

### Post by broy on 2006-04-24
there was nothing in the file, I think.

Like I said I'm new to Linux but I went to the /var/log directory and typed this:
read Xorg.0.log

and it came up with nothing so I guess there's nothing in it, but I'm not sure.

---

### Post by Kethinov on 2006-04-25
Try **nano /var/log/Xorg.0.log**

I like your avatar, BTW. Makes me want to play Super Metroid.

---

### Post by broy on 2006-04-25
It says that I don't have permission to edit the file. I tried this:

sudo dpkg-reconfigure xserver-xorg

and I went through the program and it seemed to find all of my hardware ok.
During startup it loads the hotplug subsystem and it doesn't fail but it doesn't say ok either. I'm using a usb keyboard and some linux guys here at work think that I might have a problem with my usb. They suggested I try an update using:

apt-get update

But that wouldn't work and gave me an error. One time at the login screen I went into the CLI and logged out and then back in, and then started the gnome and it got into it but froze again just like before.

---

### Post by Kethinov on 2006-04-25
You don't need to edit the file, you just need to see what's in it. That log file contains a record of the errors X11 recorded during its last session and might give us some clues as to why you're having these issues.

Try running that command as root, or sudo. Post the contents here.

---

### Post by broy on 2006-04-25
Thanks for all your help, but we figured out what the problem was, my video card drivers.

I decided to try another distro, so I got a copy of Fedora 4 and installed over ubuntu. It had the same freezing problem and the reason was that it was trying to use the old radeon drivers that came with the os. We changed it to vesa and then downloaded the drivers for the vid card and I haven't had any problems since then. I'm sure if I did the same thing in Ubuntu it would work.

I hope this help any other n00bs with the same problem :D

---

### Post by Kethinov on 2006-04-25
I helped someone through a nearly identical situation a few weeks ago as well. It's a shame Ubuntu doesn't just ship and automatically configure the proprietary video drivers from ATI and NVIDIA so people who buy these popular cards don't have to deal with such problems.

---

### Post by broy on 2006-04-25
I guess the problem is that ubuntu is still using the same linux stuff and didn't bother to include newer drivers for various types of hardware.

---

### Post by kyle_charest on 2006-04-27
i have a similar problem with my laptop. I installed kubuntu on my computer, and it didnt work. i didnt know to update the KDE and X11 for it to have a GUI. anyways i tried kubuntu 6, and it worked the first time, after a reboot it wouldnt work. So i have decided to stick with breeze. the thing gives my a promt, no GUI. i booted up in recovery, and used aptitude to update everything (KDE andX11) and installed the stuff, and the thing is that it freezes after the login. someone pleasee help me i tried changing the initdefault using vim but the "id:2:initdefault" was at 2, and i was reading something that said if it is at 5 , then change it to 3. i just left it alone. i am a noob :( ...

Oh and my specs
_________________________
HP Pavilion ze2113us Laptop
Mobile AMD Sempron 2800+
1.87 GB of RAM (after virtural memory)
ATI RADEON XPRESS 200M
Seagate 60GB 4200RPM




i reposted this in a new thread 
[http://www.ubuntuforums.org/showthread.php?p=963726#post963726](http://www.ubuntuforums.org/showthread.php?p=963726#post963726)

---

### Post by broy on 2006-04-27
I fixed it by running the xorg configure thingy. It's something like sudo /var/log/Xorg.0.com or something and it took you to a driver install program where it tries to automatically detect your hardware. Everything else seemed to work fine but set your video drivers to VESA instead of ATI and then get your ATI drivers later. The freeze seems to be the result of the older ATI drivers and when changing it to VESA you can at least get into the gui and get your drivers. I'm a noob at this too so I hope this helps you.

---

