---
title: "Error after enable new video card!!"
date: 2009-02-26
forum: General Help
---

### Post by Pinejoker on 2009-02-26
[IMG]http://img530.imageshack.us/img530/3371/flog.png[/IMG]
I just put a new video card to my computer, PNY Verto Nvidia GeForce 8400 GS

and then this is what i got, after enabling the video card,

here's the result:

this is my error during activating my new video card.

[IMG]http://img403.imageshack.us/img403/2110/dscn4075.jpg[/IMG]
[IMG]http://img291.imageshack.us/img291/4257/dscn4076m.jpg[/IMG]

please help me to install my NVIDIA GeForce 8400  GS

---

### Post by dzark on 2009-02-26
log in with your username and password

then tell us what happens when you run ```
sudo /etc/init.d/kdm start
```

---

### Post by crazyness003 on 2009-02-26
> **dzark said:**
> log in with your username and password

then tell us what happens when you run ```
sudo /etc/init.d/kdm start
```
Well, If they're running Kubuntu, then yes that would yield credible results (since it says **kinit...**).
If running Ubuntu the run this command
```
sudo /etc/init.d/gdm start
``` and tell us what you see.

Also, try booting in recovery mode.
When you see something say "GRUB" (GRand Unified Bootloader), hit Esc, then you'll see your GRUB  menu. If you have multiple kernels installed (I highly doubt it) you will see them all, including thier "recovery modes". 
Just select the latest recovery selection, and hit Enter.
It will go through some things and present you with another menu, there you can have it do many cool things. I forgot exaclty what you can do, but its almost self-explanitory.

Sorry I cant be more useful

let us know what you do

---

### Post by Pinejoker on 2009-02-26
i am Ubuntu 8.10 guys.. its not working any other code to work on it?

---

### Post by Pinejoker on 2009-02-26
help me to fix my problem.. please

---

### Post by dzark on 2009-02-26
you need to help us help you..

Is it Ubuntu, Kubuntu, Xubuntu etc? 

Have you previously tried installing Gnome/KDE on top of what was default?

Can you log in with your username/password?

What happens when you type ```
startx
```

---

### Post by Pinejoker on 2009-02-26
> **dzark said:**
> you need to help us help you..

Is it Ubuntu, Kubuntu, Xubuntu etc? 

Have you previously tried installing Gnome/KDE on top of what was default?

Can you log in with your username/password?

What happens when you type ```
startx
```

what about the low resolution problem???

---

### Post by dzark on 2009-02-26
C'mon buddy. I'm trying to help you here. We can only work with the information you give us. 

If you don't want to tell us whats happening, what you've done and what error reports you're getting, there isn't anything I or anyone can help you with.

Lets sort out the facts:

1) We dont know what flavour of Display Manager you're running, so no-one is able to give you DM related help. Your 1st image looks like Gnome, but from the 2nd & 3rd image it looks like you've tried installing KDE aswell.

2) We dont know how installed your nVidia graphics driver is, so no-one can figure out if you installed it correctly, is the right driver or works at all.

3) We dont know what happens when you try starting your prefered display manager, so we really cant do ANYTHING.

4) Now you claim to have a low resolution problem. Does this mean you've now managed to start your display manager? What does your xorg.conf look like?

If you want help, try answering the questions people ask.

---

### Post by Pinejoker on 2009-02-26
after i got the error low resolution i got this..
[IMG]http://img527.imageshack.us/img527/4392/screenshotage.png[/IMG]


and then after that.. i just restart my computer and this is what i got now.. you think its fix now????
[IMG]http://img410.imageshack.us/img410/2180/screenshot1w.png[/IMG]

---

### Post by dzark on 2009-02-26
Ya, thats how it should be :D

---

### Post by Pinejoker on 2009-02-26
okay thanks for the help.. =) any games to suggest to play on linux?? online game??

---

