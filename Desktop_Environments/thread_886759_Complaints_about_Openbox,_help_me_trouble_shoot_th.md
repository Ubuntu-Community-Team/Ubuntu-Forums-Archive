---
title: "Complaints about Openbox, help me trouble shoot them!"
date: 2008-08-11
forum: Desktop Environments
---

### Post by cchung85 on 2008-08-11
Hey guys, so I am trying out Openbox right now, it's taking me on quite the journey just setting it up. Anyways, there are a few things keeping me from switching completely.

I have always been a minimalist so I love how you can set things up so the menu is easily accessible with the click of a mouse and keep the desktop clean.

Here are some things I am trying to trouble shoot, please post if you have had similar experience with it or have a way to trouble shoot it.

- Wireless won't work unless I log into gnome/ubuntu first.

- The terminal doesn't have true transparency like compiz. If I placed the terminal over firefox it will show the desktop image but not the firefox image. I have tried fixing this with transset but can't seem to change it.

- I love how compiz organizes my windows with the scale function, I have it set up so if I roll my mouse over to a corner it tiles all my windows for selection. I've tried the tile application in Openbox but it makes a mess of things and I have to resize everything.

- For some reason I can't seem to install the dependencies needed for the pypanel. I am sure if I can set up the pypanel with a clock and what not I will be able to switch over completely.

- Is there a way to display icons on the desktop still when I have files downloaded to it or when I mount my external hard drive. Though this could be a good thing as it forces me to use the terminal more and more.

Anyways, please share with me any tips and tricks if you have solutions to these problems. Thank you :)

---

### Post by snowpine on 2008-08-11
> **cchung85 said:**
> - Wireless won't work unless I log into gnome/ubuntu first.

- Is there a way to display icons on the desktop still when I have files downloaded to it or when I mount my external hard drive. Though this could be a good thing as it forces me to use the terminal more and more.


You need to add your wireless applet to ~/.config/openbox/autostart.sh

Icons on the desktop is kind of the opposite of everything Openbox stands for! :) However, I know that Fluxbuntu accomplishes this using the "pinboard" feature of rox-filer. Maybe that will point you in the right direction. Good luck!

---

### Post by eriqjaffe on 2008-08-11
I'll try to answer what I can...
> **cchung85 said:**
> - Wireless won't work unless I log into gnome/ubuntu first.```
You have to add your wireless manager applet (gnome-network-manager, or whatever it's called) to your ~/.config/openbox/autostart.sh file.

[QUOTE=cchung85;5567921]- The terminal doesn't have true transparency like compiz. If I placed the terminal over firefox it will show the desktop image but not the firefox image. I have tried fixing this with transset but can't seem to change it.That's pseudo transparency.  You need to install xcompmgr (and add it to your autostart.sh file) to enable compositing in Openbox.

[QUOTE=cchung85;5567921]- For some reason I can't seem to install the dependencies needed for the pypanel. I am sure if I can set up the pypanel with a clock and what not I will be able to switch over completely.
```Why not just install pypanel through synaptic or "sudo apt-get install pypanel" in the terminal?

[QUOTE=cchung85;5567921]- Is there a way to display icons on the desktop still when I have files downloaded to it or when I mount my external hard drive. Though this could be a good thing as it forces me to use the terminal more and more.[/code]Depends on the file manager you're using.  PCManFM supports a desktop, although mounted volumes don't show up there.

---

### Post by DocYoung on 2008-08-11
I put 

nm-applet &

in my startup for my wireless to work.

I'm running fluxbox so it may be a slightly different for openbox.

---

### Post by cchung85 on 2008-08-11
Hey guys, thanks for the tips.
I didn't even think to install pypanel in through apt-get hah.
I am going to go tweak things for a bit be back with an update :)

---

### Post by cchung85 on 2008-08-12
So I got the wireless set up, I've got the pseudo-transparent terminal set up. Now I just have to figure out how to set up the pypanel so it doesn't look so ugly!
I have a monitor hooked up to my laptop, and the pypanel only spans one side of the monitor, is there a way to have it span the whole thing?

---

### Post by woaibbhemm on 2008-08-12
hello~
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by RedSquirrel on 2008-08-12
True transparency:

[http://icculus.org/openbox/index.php/Help:FAQ#How_do_I_get_true_32-bit_transparent_windows.3F](http://icculus.org/openbox/index.php/Help:FAQ#How_do_I_get_true_32-bit_transparent_windows.3F)

---

### Post by cchung85 on 2008-08-13
So far I am loving openbox, I love how simple it is. I have fixed most of the issues I listed above. I really wish there was a way to use a similar menu system found in openbox in ubuntu.
It'd be nice to run it with compiz.
I will have to test this set up for a big longer before I could make up my mind.

Is there a way to set up openbox without disrupting the settings in ubuntu? I noticed that once my openbox is set up nicely, it has messed up all the settings in ubuntu.
It would be nice to have 2 separate settings for the system I think that would be ideal. To log into openbox for day to day uses and ubuntu when I'm lost and don't know how to do certain things in openbox. (Incase you have not noticed I've only been using linux for 2 months! :O )

---

### Post by cchung85 on 2008-08-16
Bump.

---

