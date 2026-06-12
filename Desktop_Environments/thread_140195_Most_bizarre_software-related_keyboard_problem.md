---
title: "Most bizarre software-related keyboard problem"
date: 2006-03-05
forum: Desktop Environments
---

### Post by Wilb on 2006-03-05
Got an issue which has had me scratching my head for some time... This is origianlly a problem I've been experiencing on a SuSe 9.0 install, but its just reared its ugly head again in Breezy Badger...

Bit of background: I've got a box which I use as a router and also for vdr (including lircd). Up until today, I've been using SuSe 9 for it but I had numerous problems so decided to wipe it all off and go for a Ubuntu install instead (cos I've recently decided its the best thing since sliced bread!)

Anyhow, on my previous install, I used to have a *big* problem with the keyboard. It used to be fine whilst in text mode, however when it booted into the KDE login screen, it wouldn't accept most of the input I'd give it. I would sometimes have to press a key 4 or 5 times before it would take the keypress - other times it would take it first time. This problem hadn't always existed in the setup as I managed to carry out a complete install and set it up to do everything i needed - it just reared its ugly head shortly after setting it up. 

So today I wiped it all off and stuck Breezy Badger on instead, and went on my merry way to set up all of my bits and bobs required. Everything has been working fine up until a few minutes ago when I did a reboot and lo and behold, I get into the Gnome login prompt and the same problem has started again. I can't even get it to accept enough of my keypresses to get me past the login screen. ARGH! 

Heres what I know its not... Its not a hardware problem because the keyboard works fine in the BIOS and on other computers... If I VNC into this machine I can also remotely type away at my leisure, so it seems to me like some kind of driver conflict of some sort. The one thing I'm thinking it could be is LIRC. That was probably one of the last things I installed prior to rebooting the machine - its also something which was on my previous install too. I issued the following commands after installing:

    setserial /dev/ttyS0 uart none
    modprobe lirc_dev
    modprobe lirc_serial
 
And also edited a file (can't remember which one off the top of my head!) to insert lirc_serial at startup... Bearing in mind this is a PS/2 keyboard I'm using, does anyone think this may be where the confict is coming from? I'm at a loss to explain what it could be other than that - and either way does anyone have any suggestions for how I could resolve this?

Many thanks in advance...

Wilb.

---

### Post by Wilb on 2006-03-05
Just to add to this, I've just tried booting in failsafe mode from Grub and that works fine - I  can even startx to get into Gnome as root and my keyboard is no problemms there.

Another symptom which I find most odd is the fact that its not only my keys which are sluggish with input, but the numlock / caplock keys are also showing the same traits - it can take seconds for them to go on and off, sometimes not even responding at all... Weird.

---

### Post by Wilb on 2006-03-10
Further information on my discoveries are that its not an lirc / setserial problem as I reformatted my box again and the issue came back before I'd even let it sniff lirc. I've also discovered that if I kill my X session (which is sometimes hard work due to the lack of response to keyboard input!) then when it comes back up it takes keyboard input fine. Most odd. 

I'm now thinking that this could be to do with locales as thats about the only other variable that I'm changing. Anyone got any ideas? As a workaround I suppose I could just add some lines to my startup scripts to kill X as soon as its loaded and launch it again - not sure how I'd implement that though?!?

---

