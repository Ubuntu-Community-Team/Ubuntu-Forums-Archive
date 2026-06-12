---
title: "CTRL-ALT-F1 does nothing. Can't open a virtual terminal"
date: 2006-07-21
forum: Desktop Environments
---

### Post by nwgray on 2006-07-21
Good morning everyone,
   I am attempting to install an Nvidia driver for my Geforce4 Mx440 AGP 8x card. I'm using tseliot's instructions located here:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

I'm using Method 2. When I get to step 5, I press CTRL-ALT-F1 but nothing happens. I have looked on Nvidia's page for the driver download and it tells me that I need to exit out of gnome and go to a command prompt to install the driver. How do I do that if I can't open a virtual terminal? What should I check?

Thx](*,)

---

### Post by nospam on 2006-07-21
I'm an Ubuntu newbie who's just been trying it out for a few days. One thing I noticed is, in order to get into a virtual terminal from X, CTRL-ALT-F1 to F5 doesn't work. 

For some reason, you have to do a CTRL-ALT-F6 first, which gives you virtual terminal number 6 (at least that's what I think TTY 6 means). Then ALT-Fx will now work to switch virtual terms. Although any one should work as well as tty1. To switch back to X, you need to do CTRL-ALT-F7.

It doesn't always work though, sometimes I have to hit it a few times before it switches over from X.

Alternatively, looking at the steps there, I think you can simply kill X and exit to console :D

---

### Post by nwgray on 2006-07-25
nospam
  thx for the info. I had some other issues so I did a fresh reload and then installed the nvidia driver using Automatix. Everything seems to be okay now.

:)

---

### Post by kcmanc87 on 2008-07-18
I'm having the same trouble now :'(

---

