---
title: "inspiron e1505 live CD"
date: 2007-07-28
forum: Dell  Ubuntu Support
---

### Post by Trmptxn on 2007-07-28
I would like to try Ubuntu on my computer by using the live CD before actually installing...
however 

when i try to boot to the live CD it tells me the X server desktop could not be loaded and it gives me this error code:
error:microcode "bcm43xx_mi crocode5.fw" not available or load failed. 

my system specs: 
inspiron e1505
Windows XP pro (i want to dual boot)
2 ghz core 2 duo processor
2 gigs RAM
ati x1400 GPU
cd-rw/DVD drive

Ive read that it could be the X1400 card but all the solutions i found had to do with actually installing Ubuntu. i do not want to do this yet, i just want to try it first and then (likely) install it, but if i can not try it first i will not install.  I have medium computer skills and this is my first Linux install.

thank you for any help you can give me

---

### Post by plewisfdx on 2007-07-29
I have the Inspiron 1505 with the nVidia graphics, and the live CD and install worked great after installing the 915resolution package in Synaptic.  X loaded without it, but at a lower resolution.

Did you download the iso or is a production CD you are using?  If its a download, maybe the error is in the download or burn.

Does it load all except that error line and X?  If you have a command line, you can try typing "gdm" or "startx" and maybe you can get in on a second try.

There also may be some boot options you could try.  Google that error and ubuntu and see if you can enter commands at boot time to get around this problem if all of the above don't work.

---

### Post by neptho on 2007-07-30
If you just want to 'try out' the live CD, when it bombs out, get to a prompt and make sure the network is running (ethernet is easiest):

First, add and update your repositories:

```
#echo 'deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse' >> /etc/apt/sources.list
#apt-get update
```

Now, install the ATI driver:

```
#apt-get install xorg-driver-fglrx linux-restricted-modules-`uname -r`
```

Then, when that completes,

```
# aticonfig --initial --input=/etc/X11/xorg.conf
```

Then...

```
#/etc/init.d/gdm stop && /etc/init.d/gdm start && logout
```

This should get X running for you.  You'll have to do this **every time** with the live CD, because you are running from a RAM disk.

---

### Post by cptbreecher@gmail.com on 2007-07-30
> **Trmptxn said:**
> I would like to try Ubuntu on my computer by using the live CD before actually installing...
however 

when i try to boot to the live CD it tells me the X server desktop could not be loaded and it gives me this error code:
error:microcode "bcm43xx_mi crocode5.fw" not available or load failed. 

my system specs: 
inspiron e1505
Windows XP pro (i want to dual boot)
2 ghz core 2 duo processor
2 gigs RAM
ati x1400 GPU
cd-rw/DVD drive

Ive read that it could be the X1400 card but all the solutions i found had to do with actually installing Ubuntu. i do not want to do this yet, i just want to try it first and then (likely) install it, but if i can not try it first i will not install.  I have medium computer skills and this is my first Linux install.

thank you for any help you can give me

I have an ATI issue also, but if you want to try UBUNTU without damaging anything, and if you have at least 4, preferably 8, GB free, try [http://wubi-installer.org/](http://wubi-installer.org/).  I've installed different times - had trouble with the UBUNTU, but never the install, or removing it.  Still working with the ATI issue - that's why I'm checking the forums.

---

### Post by strabes on 2007-07-30
Do what neptho told you to. You can enter those commands in a virtual terminal by hitting Ctrl+Alt+F1 after X crashes. The file you'll need to add those repositories to is /etc/apt/sources.list. So you can run ```
nano /etc/apt/sources.list
```

Just uncomment all the lines that start with "deb." Ctrl+o saves, Ctrl+x exits.

Then run the rest of the commands he wrote.

---

### Post by Paul S on 2007-07-30
The bug is with "feisty".  Ubuntu "edgy" will work from the live cd.  If you can't get to the command prompt (Ctrl-Alt-F1) on feisty live cd, you can try edgy live cd.  If you want, you could install edgy, then upgrade to feisty, then fix your ati video.

regards,

---

