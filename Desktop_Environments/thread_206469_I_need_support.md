---
title: "I need support"
date: 2006-06-30
forum: Desktop Environments
---

### Post by artux on 2006-06-30
I could easily say, there's a great talk about ubuntu on the Internet. One of the major reasons for my trial was Distrowatch putting it first rank, and a bunch of other things such as every 6 month upgrading, stability reputation, and single CD installation.

Every experience was great except after installation finishes.

The problems I am facing:

1. The system crashes often (freezes), and I think it's due to the video card configuration.

2. No libraries installed at all, so I couldn't install eagle-usb to configure my ADSL modem and start it.

3. Hibernate fails, this really dissapointed me.

I need your help, because I need to stay with ubuntu for a while and give it a big shot, rather than switching to other distros. I need to overcome this so please help.

Here's my PC configuration:
[http://geocities.com/iamarto/pcconf/]("http://geocities.com/iamarto/pcconf/")

---

### Post by jtholmes on 2006-06-30
looking at your PC config I suspect that the ATI 
video may be a source of problems. 
Go to your local Asian PC store (or Frys)
and get an nVidia card with about 256Meg Memory.

I have ubuntu on two machines and both are
using nVidia and work fine. 
Some of the ATI cards pose problems.

jt

---

### Post by tseliot on 2006-06-30
Try this for your card:
```
sudo nano /etc/X11/xorg.conf
```
Get to the Section Device of the file and set the driver to "vesa" (instead of "ati")

Then log out and press CTRL+ALT+Backspace and log in again.

---

### Post by az on 2006-06-30
[QUOTE=artux]
2. No libraries installed at all, so I couldn't install eagle-usb to configure my ADSL modem and start it.
[/QUOTE]

Boot into ubuntu and insert the desktop cd again.  You will be shown a box that asks if you want to install packages.  Install build-essential, linux-headers-386 and search for eagle-usb and install those packages.  Everything (including the source for your driver) is on the cd.

---

### Post by artux on 2006-07-02
Oh, I thought no one replied so I made another post "System Crash". Guys thanks, for this support. I solved all my problems regarding the internet connection and installed eagle-usb with no problems at all.

For the Hibernate function, I will not use for now, no problem. 

Now all what remains is this system crash problem and I will try to fix it through this advice:

> sudo nano /etc/X11/xorg.conf

But before I do this, I need to say that I have already installed the original ATI flxgr (spell?) driver instead of the originally ubuntu driver. Should I still use this command?

---

### Post by artux on 2006-07-02
Ok. I did it anyway.

First impression:
1. Hibernate function WORKS!
2. System crash, not yet happened but I wish not! I will report if it happened.

SO thank you! :)

---

