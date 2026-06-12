---
title: "Resolution issues."
date: 2007-04-24
forum: Desktop Environments
---

### Post by joerdie on 2007-04-24
Hello all. I am new to Ubuntu and trying to get the hang of things... 

I am using Ubuntu 6.something... the stable release before 7.4, on an old HP P3 900. 

My issue is that I cant get the resolution up over 800X600?!? System>Preferences>Screen Resolution only shows two options, 640X480 and 800X600. When this box was on Windows ME many years ago, and recently XP, it displayed 1024X768 with no problem. Am i missing something?

Also, I am not sure what specs you may need to help me but, just give me a holler if you need anything else. Thanks!


p.s. Sorry if this has been asked before... I searched the forums but didn't see anything.

---

### Post by heimo on 2007-04-24
> **joerdie said:**
> p.s. Sorry if this has been asked before... I searched the forums but didn't see anything.

:shock: What? I think I've seen about two thousand threads on this subject. Seriously. And I'm involved in at least couple hundred of those.

To the problem - and a starting place for solution:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by joerdie on 2007-04-24
Sorry but I honestly couldn't find anything about this... MODS, feel free to delete... Sorry to be a bother. 


TY for the link... Will follow down the rabbit hole.

---

### Post by jerrylamos on 2007-04-24
In my case this worked.  I knew that my graphics support chip was Intel 82845G.  The video driver for many of the Intel chips is i810.
So......
Ctrl-Alt-F1
should get you a command line.  To start the X windows config program:

sudo dpkg-reconfigure -phigh xserver-xorg

It'll want your password then some menus should start to run.

When I got to driver selection I picked i810.

Now from my bios I know that the graphics window is 64 mb, which is 65536 in K bytes which the menus will  probably ask you.
Presuming the dpkg went thru and worked, you need to stop the display manager:
sudo killall gdm
and then restart:
startx
If it does start, now in Ubuntu, System, Preferences, Screen Resolution might be of some help.

For more info, [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89590](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89590)

Cheers, Jerry

---

### Post by joerdie on 2007-04-25
Thanks to the both of you. I shall try tonight...

---

