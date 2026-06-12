---
title: "Ubuntu 8.10 and NVidia 177.82"
date: 2008-12-21
forum: General Help
---

### Post by hermetic on 2008-12-21
I'm having an issue with an installation of Ubuntu 8.10, specifically after having installed the NVidia 177.82 Linux drivers for my GeForce 8600 GTS (x2, in SLI).

For starters, on a clean install of Ubuntu, I have no issues with "none" selected for special effects. So, I downloaded the NVidia drivers from their site, edited /etc/event.d/rc-default so that both instances of 'telinit 2' were changed to 'telinit 3' (this suggested as a way to boot into Ubuntu without X running) and rebooted.

Installed the driver, allowed it to compile the kernal, allowed it to edit the xorg.conf. It told me everything was installed correctly. I went ahead and changed the rc-default 'telinit' values back to 2 and reboot. Now I can't get my GUI back. It defaults me into tty1. Ctrl + Alt + F7 just brings me to a black screen with a blinking cursor.

I've restarted the gdm server, rebooted, same thing. Tried startx, gives me a fatal server error: no screens found, giving up. 

I'm pretty much lost. Any help would be appreciated.

---

### Post by hermetic on 2008-12-22
I hate to bump, but does no one have any ideas at all?

---

### Post by 3rdalbum on 2008-12-22
Open the Xorg.conf file:

```
sudo nano /etc/X11/xorg.conf
```

In the bit where it says Driver   "nvidia", change it to Driver    "nv"

Save your changes (press Control-O, then press Enter), and quit the text editor (press Control-X). Reboot (sudo reboot).

You should have your graphical display back, with the regular 2D acceleration. From there you can try troubleshooting the Nvidia driver or try reinstalling the driver.

---

### Post by hermetic on 2008-12-24
> **3rdalbum said:**
> Open the Xorg.conf file:

```
sudo nano /etc/X11/xorg.conf
```

In the bit where it says Driver   "nvidia", change it to Driver    "nv"

Save your changes (press Control-O, then press Enter), and quit the text editor (press Control-X). Reboot (sudo reboot).

You should have your graphical display back, with the regular 2D acceleration. From there you can try troubleshooting the Nvidia driver or try reinstalling the driver.

3rdalbum: Thanks for the info.

Gave this a shot tonight and wound up right back where I started, tty1. Tried to move over to the GUI session and still had the black screen with the blinking cursor.

Any other ideas?

---

### Post by Mirai_-_ on 2008-12-26
Possibly you already know, but if your video card can be supported by a driver that is in the Ubuntu repositories (and yours is), then you should just use that.  For Intrepid, version 173.14.12 of the nVidia driver is easily installable via apt with the command: "sudo apt-get install nvidia-glx-173".  Configuring X server to use nvidia is all that you need after that--more or less.

I've been running GeForce 9600 GT with it for a while with no problems.

---

### Post by dasim on 2008-12-29
im having the same issue with a 9600 GTS. Any ideas?

---

