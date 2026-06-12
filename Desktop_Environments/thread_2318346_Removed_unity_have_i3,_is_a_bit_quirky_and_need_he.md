---
title: "Removed unity have i3, is a bit quirky and need help tidying."
date: 2016-03-25
forum: Desktop Environments
---

### Post by revenge3 on 2016-03-25
I had a choice of unity and i3 at the lightdm login, once  I was used to i3 I decided to remove unity- this wasn't so much because I didn't want both, that was a good setup, I removed it because 
there is a handful of quirky config conflicts and I couldn't customize i3, these issues were:

A grey menu bar for each newly created and stacked i3 terminal.
That really quite nice deep purple background.
the better ubuntu font.
that i3 config would not change the font type.

also I wouldlike to know how to auto start i3 with light dm, as I have started differently a lot of the walkthroughs and tutorials I find simply dont apply to my situation,
lightdm never has the config file its suppoed to, i3 doesnt have the fonts folder, where are these things?

Also, I did use that menu bar to select preferences and have it never show up again, I also used it to change to a font htat I have gone off, ironically know that annoying menu bar HAS gone, I cant change the font back.

Incidently there is some use to the old ubuntu stuff, if I get could the networking gui upp, it was easy to conenct to wifi than with network manager.
and the old profile preferences, is there a commond shortcut to get that up too? after all I just told the menu not to appear I didn't delete it

It seems there's accidental problems but everythings still sort of working nicely and I could put up with the conflict if I could solve these specific issues.

-if I could get profile preferences up can someone tell me how to add a new font-

I can see this post is messy with lots of bits on it but ultimatley im looking for a bit of direction.

---

### Post by v3.xx on 2016-03-25
Unity cannot just be removed, there are packages that are needed (dependencies).  For a i3 only install we have what is called the mini iso.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Notice that the mini iso is only 40M, nothing there till you put it there.

---

### Post by revenge3 on 2016-03-25
So you think I should fresh re-install the whole shebang? before I start, will I still need a fresh lightdm or is that included?

Im am new to this, and I get  the impression that  Iwould need to know how to configure hat.

---

### Post by v3.xx on 2016-03-25
If you do not understand the packages, then this is a very hard way to go.  Maybe you would be better off installing a core system and then installing i3.  I3 is not widely used and its difficult to get help with, but installing it to a core metapackage should get you going.

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by revenge3 on 2016-03-25
ahhh too late xD, however I got so far the first time round and the odd quirks could be useful and I know how I got to that point;

I originally installed arch and i3 on a piece of junk laptop as an experiment and got somewhere with that too, it looked so so deeply ugly though, but
at least I managed so I think I will be fine tk.

-wait on that note-  Is there a gui network manager I really HATE network setup on cmd, I have had bad pi/virgin media problems, dhcp yo ucan forget about it especially with their new routers.

---

### Post by v3.xx on 2016-03-25
Ok, this route will be a good learning experience.  I can't help with i3, but...

> auto start i3 with light dm

[https://wiki.ubuntu.com/LightDM#Changing_the_Default_Session](https://wiki.ubuntu.com/LightDM#Changing_the_Default_Session)

Arch has a different approach

[https://wiki.archlinux.org/index.php/LightDM#Default_session](https://wiki.archlinux.org/index.php/LightDM#Default_session)

And it may help you to know about googlubuntu

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=lightdm&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=lightdm&sa=Search&cof=FORID:9)

I'll drop back in here at lunch (5 hours), see what you think :)

---

### Post by oldos2er on 2016-03-25
> **v3.xx said:**
>   I3 is not widely used and its difficult to get help with

The i3 mailing list is easily accessible and newbie-friendly:  [http://www.freelists.org/list/i3-discuss](http://www.freelists.org/list/i3-discuss)
And there's also the IRC channel: irc://chat.freenode.net/i3

---

### Post by revenge3 on 2016-03-25
thanks guys, I been held back missivley, I used the minimum install iso and it kept loading the bootloader on the usb stick, I installed the server addition without addons in the end, im configuring networking now, got ethernet, so far so good, but cant tell you if beautiful yet, as for arch, I need to learn a bit more, but thats what the junk laptop is for.

tk guys, its less frustrating when you know your not completely alone in the world.

---

### Post by revenge3 on 2016-03-25
ja its hopeless xD

ubuntu server has a lot of junk on it too, installed light dm and i3, typing exec i3 makes the terminal purple so somethings happening/.

also no folders that are supposed to be there in the user guide exist, don't know where to go from here.

---

### Post by revenge3 on 2016-03-25
Okay installing ubuntu is my life know and i hate every moment of it, fml

---

### Post by revenge3 on 2016-03-25
okay is fine heres what is different now.

ubuntu min you got ot take out the usb else it installs grub in the disk.
black screen does work, you hit ctrl + alt + f1 :P
downloaded all the xserver-xorg stuff.
downloaded i3, BAM it works :D

No to go back to stressing about beauty, but my god do I got performance and efficiency!!

---

### Post by vasa1 on 2016-03-25
> **revenge3 said:**
> ..
No to go back to stressing about beauty, ...
Screenshots would be nice!

When you installed *i3*, did you install with or without its recommends?

---

### Post by revenge3 on 2016-03-25
im stil lworking on it, I will stil lscreen shot though, turns out to be very simple install.
no recomends at all, so I might learn the hard way, wicd-gtk works fine though.

im focussing on superficial looks now like fonts and screensaver, that and its got to start up in i3 else I could wait an age
and not know its booted (black screen)

---

