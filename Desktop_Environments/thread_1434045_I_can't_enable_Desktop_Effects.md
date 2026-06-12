---
title: "I can't enable Desktop Effects"
date: 2010-03-19
forum: Desktop Environments
---

### Post by invaderzim431 on 2010-03-19
Hey ^_^
ok so I'm running Ubuntu 9.10 on virtualbox and I'm trying to set up compiz, but when I try to enable the desktop effects it won't let me.. check it out..
Thanx..:D

---

### Post by N92 on 2010-03-19
First do you have your video card driver installed?

---

### Post by UCSBGauchosRock on 2010-03-19
This has happened to me before. Now I'm running them on extra though. Can your graphics card handle compiz?

---

### Post by n0dix on 2010-03-19
Do you have direct rendering?
```
$ glxinfo | grep direct
```

---

### Post by invaderzim431 on 2010-03-19
N92: How can I check that? and do it?

UCSBGauchosRock: This is my graphics card: ATI Radeon HD 4350

n0dix: What is direct rendering??

Thanx ^_^:popcorn:

---

### Post by UCSBGauchosRock on 2010-03-20
Your graphics card is definately capable of running compiz......

---

### Post by invaderzim431 on 2010-03-20
I just tried enabling the effects and it said it was looking for the drivers, then it said it couldn't enable the effects..
Does that mean it just isn't finding the drivers, and that I should find them? how would I do that??
:KS

---

### Post by invaderzim431 on 2010-03-20
I looked up the website and found drivers..
is this the one I should download??

---

### Post by UCSBGauchosRock on 2010-03-20
> **invaderzim431 said:**
> I looked up the website and found drivers..
is this the one I should download??

From the looks of things yes those are the ones you need

---

### Post by 5735guy on 2010-03-20
You need to install VirtualBox 3.1 which supports 3D acceleration

Installing VirtualBox 3.1 On An Ubuntu 9.10 Desktop
[http://www.howtoforge.org/installing-virtualbox-3.1-on-an-ubuntu-9.10-desktop](http://www.howtoforge.org/installing-virtualbox-3.1-on-an-ubuntu-9.10-desktop)

Enabling Compiz Fusion On An Ubuntu 9.10 Desktop (Disregard Graphics Driver installation)
[http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200](http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200)

---

### Post by n0dix on 2010-03-20
> **invaderzim431 said:**
> [...]
n0dix: What is direct rendering??
Thanx ^_^:popcorn:

Is what you need to get visual effect. 
Probably you need activate opengl 3d acceleration with wine.

---

### Post by Rasa1111 on 2010-03-20
though , after you have it set up..
you may find that your system worked better without it.

---

### Post by uRock on 2010-03-20
> **Rasa1111 said:**
> though , after you have it set up..
you may find that your system worked better without it.

Why the negativity?

Compiz is great!

---

### Post by n0dix on 2010-03-20
> **iRock said:**
> Why the negativity?

Compiz is great!

With enough memory ram.

---

### Post by Rasa1111 on 2010-03-20
> **iRock said:**
> Why the negativity?

Compiz is great!


not really negativity, 
just basing it off my experiences with a number of different computers.

2 of 10 machines worked fine with it,
the other 8 ran like they were about to die. 
(5 of those near brand new)

I mean, sure....  I am a newb...
but after a couple handfuls of Ubuntu installs/setups... 
it just seems to me that machines run quite a bit better without it. :KS

n0dix said.. "with enough memory RAM"

 Yea, One would think that 4 gigs of RAM would be plenty, eh? lol

---

### Post by uRock on 2010-03-20
> **Rasa1111 said:**
> not really negativity, 
just basing it off my experiences with a number of different computers.

2 of 10 machines worked fine with it,
the other 8 ran like they were about to die. 
(5 of those near brand new)

I mean, sure....  I am a newb...
but after a couple handfuls of Ubuntu installs/setups... 
it just seems to me that machines run quite a bit better without it. :KS

I think it has to do with quality of GPU and the amount of RAM. The only system I have that doesn't work with Compiz was built in 2002.

---

### Post by lavinog on 2010-03-20
I am assuming that you want desktop effects just to test them and not for continued use right?

Since you are using a vm, the vm is going to provide a different video card than what your host system has.
wikipedia:
> 
By default VirtualBox provides graphics support through a custom virtual graphics card which is VESA compatible.

You are likely to not get the full performance of your video card.

---

### Post by Yanglei on 2010-03-22
I take the same problem,
 
Now I use the vbox 3.1.4, I opened the 3D in settings, and install the guest addition in [COLOR=black]Configuring virtual machines.[/COLOR]
 
The problem soloved.

---

