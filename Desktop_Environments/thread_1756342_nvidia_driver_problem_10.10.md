---
title: "nvidia driver problem 10.10"
date: 2011-05-12
forum: Desktop Environments
---

### Post by dctrsatan on 2011-05-12
Ok so I have been trying to get my NVIDA geforec 6200 agp card to work in my dimension 4600 and I am able to see a picture and all but the card seems to not be fully installed.  I have tried everything from uninstalling the drivers to installing new ones and nothing seems to work.  The system boots fine but there is no xorg file being created (screenshot below and show hidden files is checked) when i run in terminal i get this

owner@owner-Dimension-4600:~$ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found
owner@owner-Dimension-4600:~$ 



[IMG]http://i249.photobucket.com/albums/gg213/killallmormons/Screenshot-1.png?t=1305194864[/IMG]

also 

[IMG]http://i249.photobucket.com/albums/gg213/killallmormons/Screenshot-1-1.png?t=1305195221[/IMG]

---

### Post by 23dornot23d on 2011-05-12
Can you run Nvidia-Settings ok .... and do a screenshot of it running ...... please.
( of the first screen you see .......... when it starts )

similar to this ...

[IMG]http://img707.imageshack.us/img707/5707/nvid.jpg[/IMG]

[BUG]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/539997")

---

### Post by dctrsatan on 2011-05-12
My problem has been solved it was such a pain but i did it :)  Uninstalled everything Nvidia related then blacklisted the nevour or however it is spelled, booted into recovery mode as root, installed the newest driver and woola lol

---

### Post by redocpot on 2011-05-12
LOL... I'm having the same problem on 10.04 .

How did you solve it? 

I have already blacklisted a bunch of nvidia-related modules:

> blacklist nouveau
options nouveau modeset=0
blacklist vga16fb
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
# blacklist nvidia-current
blacklist nvidiafb

(Note: I took out the "nvidia-current" because I think it's needed)

These are the only nvidia-related packages installed:
> i   nvidia-current                  - NVIDIA binary Xorg driver, kernel module a
i   nvidia-current-modaliases       - Modaliases for the NVIDIA binary X.Org dri
i   nvidia-glx-185                  - Transitional package for nvidia-glx-185   
i   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr

---

### Post by redocpot on 2011-05-12
And, when I run "nvidia-settings", I get the error:

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

BUT THERE IS NO "nvidia-xconfig" !!

---

### Post by 23dornot23d on 2011-05-12
> 
My problem has been solved it was such a pain but i did it :smile:   Uninstalled everything Nvidia related then blacklisted the nevour or  however it is spelled, booted into recovery mode as root, installed the  newest driver and woola lol


Good to hear ....we are on a roll ..... forward and onward ...... ;)

---

### Post by 23dornot23d on 2011-05-12
> 
BUT THERE IS NO "nvidia-xconfig" !!


looking for a solution .....

---

### Post by redocpot on 2011-05-12
@23dornot23d: I have no idea what you are talking about. 

This system has been working fine for 2 years. I had done the usual updates, but never rebooted in a while. Yesterday I had a power outage, and after that, X refuses to come up with the right driver. I'm stuck in 640x480 mode.

---

### Post by 23dornot23d on 2011-05-12
What graphics card do you have and what system ?

laptop ? desktop .... ? 

Graphics card > ?

you joined in on a thread that I believe is solved .....

you give little if no information and you have no idea what I am talking about !!!!!

This thread was on !0.10 ....

your problem is 10.04 ....

Start a new thread ...... please

---

### Post by redocpot on 2011-05-13
@23dornot23d : I have a GeForce GT 220 , under 10.04 .
My problem was identical to the OP's, and at almost the same time, so I figured I might be able to catch his attention.

In any case: I just downloaded the drivers from NVidia's site; ran the ./NVIDIA-Linux.....run script, and now everything works beautifully. No messing with Ubuntu packages, etc.

---

