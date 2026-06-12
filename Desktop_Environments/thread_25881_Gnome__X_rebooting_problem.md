---
title: "Gnome / X rebooting problem"
date: 2005-04-11
forum: Desktop Environments
---

### Post by elitebc on 2005-04-11
Well let's see what I did to cause this... 
I got the newest i686 kernel and gnome from ubuntu-universe... and then rebooted.

So the problem...
Ubuntu starts booting, everything loads, then X begins to start. The black screen with the mouse loading screen shows up for about 3 seconds and then it goes back to the command prompt. It then loads X again and this repeats infinitely. This makes it a kind of hard to troubleshoot having 5 seconds to do anything.

What I've tried to do...
Use my i386 kernel and older versions... didn't work.
I tried running dpkg-reconfigure xserver-xorg and it just made it so that it said something about and error with X and it will wait to load.

I tried running dpkg-reconfigure gdm and it said something about the X session needing to be stopped. But I cannot stop it since it keeps rebooting.


So... if anybody could offer some kind of suggestion of what to do that would really be appreciated. I'm not some Linux master since I've only been using it for a few weeks.

---

### Post by accuser on 2005-04-11
Now why would you be wanting the latest gnome from universe?  :-)

It sounds like something is broken with the gnome greeter, maybe a problem with permissions somewhere?

Anyway, what is wrong with GNOME 2.10.1 that seems to have shipped with Ubuntu 5.04. That not fresh enough??  :roll:

---

### Post by elitebc on 2005-04-11
Well I actually got the RC so I think it was a lower version than that.

I didn't do anything with permissions so unless something changed on it's own...

---

### Post by elitebc on 2005-04-11
could it be an ati driver problem ?

---

