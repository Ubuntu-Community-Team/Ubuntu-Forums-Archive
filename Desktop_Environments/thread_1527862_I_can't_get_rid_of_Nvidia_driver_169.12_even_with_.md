---
title: "I can't get rid of Nvidia driver 169.12 even with Envyng."
date: 2010-07-09
forum: Desktop Environments
---

### Post by randywilharm on 2010-07-09
Even with Envyng it won't let me try to install other drivers.
I've been able to uninstall 169.12 but Envyng will only produce an error message in terminal stating that other drivers can't be installed.

I've tried installing them while booting into recovery mode
but I still can't get any other drivers to load

Sometimes I got nothing but the terminal when I rebooted, so I would use:

sudo dpkg-reconfigure -phigh xserver-xorg

and reboot...this would put me right back to driver 169.12
but I need another driver as 169.12 crashes an application.

Is anyone familiar with this?

---

### Post by Frogs Hair on 2010-07-09
What operating system and graphics card are you using ? I was wondering because 169.12 was released in 2007 .

---

### Post by randywilharm on 2010-07-09
Sorry I forgot to add:

Ubuntu 8.04 Hardy Heron

AMD 

Nvidia geforce 8500 gt

and with a little deeper thought to this,

I did try to install another driver via the
terminal a few days ago ago and I used sudo -i to do it,

I'm wondering if there's a conflict there..?

---

### Post by stinkeye on 2010-07-10
There is a tutorial here on [**_[COLOR="DarkRed"]How To Install nVidia 256.35 Display Drivers In Ubuntu from a ppa[/COLOR]_**]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html")
This is for GeForce 6 and above, and includes how to install in hardy.
I am currently using these for my 9400GT on lucid with no problems.

---

### Post by randywilharm on 2010-07-10
Hey thanks a lot....I do appreciate that.

We're gaining a lot of ground here
in this struggle...the card's o.k.
I think it's a matter of having the Xserver
and the driver functioning without conflict
and eventually this thing will work.

beats doing windows...

---

### Post by randywilharm on 2010-07-11
I actually tried that link and the PPA repository triggers an error message saying there is no "public key"...

So, unfortunately it was a failure...I have switched to intrepid and the problem
followed me right into the upgrade!....Some error boxes came up too, asking me to install nvidia-glx-256 but it does'nt seem to be available in the repo's

---

