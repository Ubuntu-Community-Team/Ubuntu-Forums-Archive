---
title: "ATI Driver and xserver-xgl"
date: 2007-12-24
forum: Desktop Environments
---

### Post by blueridgedog on 2007-12-24
I am considering installing the linux driver from ATI.  I note on their web page that it is for X.Org.  Will it work with the xserver-xgl which I am currently running?

The performation of xgl is considerably better than the default xserver.

---

### Post by adam.tropics on 2007-12-24
You shouldn't need xserver-xgl with the current driver from ATI, since they have now enabled AIGLX. But if you wish to use it, yes I think it will work.

[Guide here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") (method 2), [driver here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.443.1-x86.x86_64.run").

---

### Post by blueridgedog on 2007-12-24
Thanks.  I evidently have the latest ATI driver (restricted), as I was told as much when I did:

sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx

However, I had poor desktop performance (and a reluctance for emerald/compiz to run) until I ran:

sudo apt-get install xserver-xgl

So, I am a bit confused as the link you sent (which I have saved) implied that I would not need to run xserver-xgl.

However:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 XT
OpenGL version string: 2.0.6473 (8.37.6)

I have over a decade of experience on Linux as a server, but so little as a desktop OS, I am still struggling to see the forest from the trees with the various X window servers and the various window managers.

---

### Post by adam.tropics on 2007-12-24
Sorry, perhaps I didn't explain very well. In the last couple releases, since after the Ubuntu included one, ATI have enabled AIGLX in their drivers. Doing that means that with the latest drivers you no longer need xserver-xgl. The latest drivers however, are not included in Ubuntu since at release, they hadn't been written, so to get them, you need to download and install them.

edit: although to clarify, xgl will work with the driver you have installed, but aiglx would be better and save a fair bit on memory use.

---

### Post by blueridgedog on 2007-12-24
OK, how would I tell then what server I am running and, theoretically, how would I switch back and forth?

---

### Post by adam.tropics on 2007-12-24
Well you'd uninstall xgl altogether, put the new drivers on there, make sure you have the following in your /etc/X11/xorg.conf

```
Section "Extensions"
    Option "Composite" "1"
EndSection

Section "ServerFlags"
    Option "AIGLX" "on"
EndSection

Section "DRI"
    Mode         0666
EndSection
```Then when you run compiz, aiglx is enabled, when you metacity, it isn't. First go though run 'compiz --replace' from the terminal, you will get output you can post if you have any problems. Better instructions at the link I [gave earlier]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

If however you'd rather go with xgl, there is a guide for doing [that here.]("http://ubuntuforums.org/showpost.php?p=3547657&postcount=7")

---

### Post by blueridgedog on 2008-01-08
I finally "got it".  I used envy to installed the latest ATI, then uninstalled xserver-xgl (sudo apt-get --purge remove xserver-xgl) and I was able to run compiz with the xorg server.  However, I am still not statisfied with the performance of compiz (I have a pretty good sytstem).  I suspect I will stick with metacity.

Any idea what the difference is between window manager (compiz/metacity) and window decorator (emerald/gtk)?

---

