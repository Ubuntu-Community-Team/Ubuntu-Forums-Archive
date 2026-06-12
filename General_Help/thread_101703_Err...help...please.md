---
title: "Err...help...please?"
date: 2005-12-10
forum: General Help
---

### Post by eXSBass on 2005-12-10
Rightio...i've looked in the FAQ on how to install ATI drivers and it says to use Synaptic. Now the package I want to install is called:
"ati-driver-installer-8.19.10-x86_64.run"
When I go to Synaptic, enter the password on request etc. I can't find this file. I want to install it. Its even on my desktop! When I search for the file in Synaptic no results!

So I double click the .run file to see if that works and it seems I need to be a "Super User" which actually makes me think. How the hell do I become a super user? :p

If you could answer those I would appreciate it, it would bring me closer to getting my system up and running.

---

### Post by `GooZ´ on 2005-12-10
You could try this:
open terminal
cd Desktop
sudo ./ati-driver-installer-8.19.10-x86_64.run
then you will be asked for your password.

---

### Post by eXSBass on 2005-12-10
[QUOTE=`GooZ´]You could try this:
open terminal
cd Desktop
sudo ./ati-driver-installer-8.19.10-x86_64.run
then you will be asked for your password.[/QUOTE]

Using that will I get a nice GUI or that text line interface?

---

### Post by ren wins on 2005-12-10
sudo is the command to run things as super user in ubuntu/debian

in other linux builds you use the command su to change into superuser
but in debian builds (and maybe others?) you have to preface some terminal commands with sudo and enter your admin password (the one you log into ubuntu with).

---

### Post by eXSBass on 2005-12-10
Okay i'll try the sudo option and see how it goes :) I'll report back soon :D

---

### Post by ren wins on 2005-12-10
oh, also

> cd Desktop
sudo ./ati-driver-installer-8.19.10-x86_64.run
then you will be asked for your password.

wont give you a gui, but you wont need it
terminal works just as well

---

### Post by eXSBass on 2005-12-10
[QUOTE=ren wins]oh, also

[QUOTE=`GooZ´]You could try this:
open terminal
cd Desktop
sudo ./ati-driver-installer-8.19.10-x86_64.run
then you will be asked for your password.[/QUOTE]

wont give you a gui, but you wont need it
terminal works just as well[/QUOTE]


Okay, I didn't want to mess about with entering passwords every 5 mins of the installation so I did it through root terminal and worked a charm. Actually I was quite suprised because when I did do so it did present me with a GUI. I reckon it installed okay, the ATI icon is in my applications list.

Now, a slight problem. During installtion it said something along the lines of:
- Save X Window config file
- run fglrxconfig

I didn't do the above because I didn't know how to do it. So if anyone could shed some light on these two then I can reinstall the ATI stuff and include these two.

And before I forget before I went into installation I went to Synaptic and couldn't find the xorg-driver-fglrx package, because I think I was told I need to install this first. I couldn't find it so I just installed the ATI stuff.

If you could shed some light on the above I would appreciate it.

Cheers.

---

### Post by taurus on 2005-12-10
sudo fglrxconfig

---

### Post by eXSBass on 2005-12-10
[QUOTE=taurus]sudo fglrxconfig[/QUOTE]

Right, what do I do with it?

---

### Post by taurus on 2005-12-10
You run it from a terminal and enter horizontal and vertical for your monitor and other things!!!  In other words, you are modifying your /etc/X11/xorg.conf!!!

---

### Post by eXSBass on 2005-12-10
[QUOTE=taurus]You run it from a terminal and enter horizontal and vertical for your monitor and other things!!!  In other words, you are modifying your /etc/X11/xorg.conf!!![/QUOTE]

Excellent. Few last things. "Save X Window config file". Now I remember changing something in X Window as I had to change my driver from "ati" to "vesa" to get into GUI mode, and now i'm in GUI i'm installing the proper drivers for my card.

---

### Post by taurus on 2005-12-10
And if "ati" doesn't work, you may want to change it to "radeon" then.

---

### Post by eXSBass on 2005-12-10
[QUOTE=taurus]And if "ati" doesn't work, you may want to change it to "radeon" then.[/QUOTE]

But the thing is how do I get to the X Window config file and how do I save it :p I forgot how to do it

---

### Post by taurus on 2005-12-10
Are you talking about editing your /etc/X11/xorg.conf?

sudo gedit /etc/X11/xorg.conf

---

### Post by eXSBass on 2005-12-10
Cheers! Edit: How do I save the config file?

---

### Post by taurus on 2005-12-10
[QUOTE=eXSBass]Cheers! Edit: How do I save the config file?[/QUOTE]
Do you see an icon of a floppy disk with the word "Save" underneath it???  Otherwise, Click File (upper left corner) and pick Save!

---

### Post by eXSBass on 2005-12-10
[QUOTE=taurus]Do you see an icon of a floppy disk with the word "Save" underneath it???  Otherwise, Click File (upper left corner) and pick Save![/QUOTE]

Kool. I'll try it and report back!

---

