---
title: "strip GNOME and all it's CRONIES down to X ONLY"
date: 2009-09-01
forum: Desktop Environments
---

### Post by misteralexander on 2009-09-01
I installed Ubuntu on my PS3. Obviously, it's the PPC version.

in any case, I QUICKLY found that GNOME + NAUTILLUS and all the other "filler" or "fluff" that comes with a stock Ubuntu is WAY, WAY, WAY to resource intensive for a smooth run on the PS3.

First off, the PS3 only has [256MB XDR @ 3.2Ghz ~ w/ 25.6GB/s]("http://www.rambus.com/us/products/ps3.html") memory bandwidth . . . punny ammount with TERMINATOR muscle. But still not the right "mindset" for a "real" computer.

I am wondering, without building from scratch, does anyone know how to (from command line) completely UNINSTALL GNOME? I mean, GNOME, ALL GNOME REQUIRED APPS, GDM . . . all of it, so I'm basically just left with the OPERATING SYSTEM and X.  I want to install the most aggressively lighweight apps and/or managers.

I have searched around here & googled, but all answers seem to not actually tell you how to fully un-install, instead telling people to just install something like XFCE . . . okay, that's great . . . I've done that . . . now how do I get rid of GNOME and all it's cronies?

Thanks!
Alex.

---

### Post by lisati on 2009-09-01
And what do you propose using as a desktop manager instead of Gnome?

---

### Post by misteralexander on 2009-09-01
> **lisati said:**
> And what do you propose using as a desktop manager instead of Gnome?

[http://en.wikipedia.org/wiki/Comparison_of_X_window_managers]("http://en.wikipedia.org/wiki/Comparison_of_X_window_managers")

there are LOTS AND LOTS AND LOTS.

there are more lightwieght file managers than NAUTILUS too:

[http://en.wikipedia.org/wiki/Comparison_of_file_managers]("http://en.wikipedia.org/wiki/Comparison_of_file_managers")

Any help is still help,
thanks,
Alex.

---

### Post by krazyd on 2009-09-01
Have you tried this? Simply install a command-line-only system then add whatever Window Manager or Desktop Environment you want.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by earthpigg on 2009-09-01
> I am wondering, without building from scratch, does anyone know how to (from command line) completely UNINSTALL GNOME? I mean, GNOME, ALL GNOME REQUIRED APPS, GDM . . . all of it, so I'm basically just left with the OPERATING SYSTEM and X. I want to install the most aggressively lighweight apps and/or managers.

look at every package installed, what it does, what it depends on, what depends on it, and remove them one by one. apt-get autoremove could potentially help you out, but it will still be a huge pain and you will likely end up in reverse [depenceny hell]("http://en.wikipedia.org/wiki/Dependency_hell").


backing your stuff up and doing a fresh command line install would be much quicker and easier:

> sudo apt-get install Xorg

if you are looking for a super lightweight DE that still manages to be a complete DE, i suggest LXDE. ubuntu command line install + LXDE will use about 60mb of ram at boot.

---

### Post by louieb on 2009-09-01
I've done that in the past just to see what happens. Easier to do if you just do a minimal install, then install X on top.  What I found out is X without a window manager is pretty useless. 

Like the others have suggested you will want some window manager installed on top of X.

---

### Post by snowpine on 2009-09-01
Follow these instructions to completely remove Gnome and replace it with Xfce:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

(skip the last step 'sudo apt-get install xubuntu-desktop' if you want a different window manager)

Good luck!

---

### Post by misteralexander on 2009-09-01
Thanks for all the good suggestions, I ended up choosing to just reinstal with a command-line. That seems to have worked great, but now i'm stuck between a rock and a hard place.

Please review my other post in the "SECURITY" section, if you're instrested. [http://ubuntuforums.org/showthread.php?t=1255598]("http://ubuntuforums.org/showthread.php?t=1255598")

Elsewise, thank-you so much for your time & help.

-Alex.

---

