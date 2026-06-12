---
title: "Nvidia GT 525M external display on Dell XPS"
date: 2011-10-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Hanine on 2011-10-22
Hello Ubuntuers!

Has anyone succeeded to drive 2 external digital monitors through a DELL XPS equipped with a NVIDIA GT525M. Ubuntu 11.10 installed.

The DELL XPS has a mini DIsplayPOrt and a HDMI video outputs.
Each one is connected to an external screen (1920-1080p) through HDMI and DVI.

Laptop screen is disabled.

Thanks in advance.

---

### Post by PatMills on 2011-11-16
It's hard to believe someone hasn't gotten a Dell XPS with Nvidia GT 525M to work with both the laptop display and external (HDMI) monitor to work.

I've chased down every link. I can get the laptop LCD to work or the external LCD, but not both. I have about 30 xorg.conf files.

Any body have this working

Ubuntu 10.04

Would it help to go to Ubuntu 11.XX

---

### Post by Solimyr on 2011-11-18
Hi all,
I have a Dell XPS with an NVIDIA Card.That could be the 500 series with intel and optimus technology. I bought last march!
My problem is that I'm not able to use the HDMI...I tried to connect but nothing happens (I checked the monitor application but does not detect the outside monitor). I tried to check the driver of the NVIDIA and I get something like:" Driver correctly installed but not in use". So I moved on internet and I discrovered that the Nvidia card is not working on my ubuntu 10.10. 
I did something but still nothing happens, this it is what I've done:

```
sudo nvidia-settings

```

but I get the following error:

> 
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

after that I have downloaded the driver from the Nvidia internet site (I get a .run file) but when I try to install that I get:
> 
ERROR: You appear to be running an X server; please exit X before 
installing. For further details, please see the section INSTALLING 
THE NVIDIA DRIVER in the README available on the Linux driver 
download page at [www.nvidia.com](www.nvidia.com).


ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details. You may find 
suggestions on fixing installation problems in the README available 
on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

So like now I'm in panic because I want just use the HDMI!!!!Also I have discovered that exist a software called bumblebee (I understand that were two project derived from it) that permit to enable the NVIDIA card, or the intel one, manually.
I didn't install it because no one was able to tell me if that works or not for the HDMI.

Do you know how can I solve my problem (connect my ubuntu on a different monitor)? Do you know some trick or something else?Please help....

I post some command from my ubuntu:

```
user@user-laptop:/var/log$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)

user@user-laptop:~$ lshw -c display | grep driver
WARNING: you should run this program as super-user.
       configuration: driver=nvidia latency=0
       configuration: driver=i915 latency=0
```
Please help!!

---

