---
title: "thrown back to login screen"
date: 2009-07-11
forum: Desktop Environments
---

### Post by BigT0 on 2009-07-11
ok, so i know this is a frequently asked question but I've been googling for two weeks and found nothing that helped me...

I'm with jaunty and linux kernel 2.6.30-generic.

after a normal update i rebooted.
boot process was normal and i got to login screen.
i entered my username and password.
now what happens is that i see a black screen, a centered courser and hear the login music. then for half a second i see cli (it's actually what i see if i press ctrl+alt+f8 ) and i get thrown back to login screen.
but i can login normally as root.

now there are a few thing i did after googling allot....

1: freed disk space.
2: added my user to admin group
3: checked ownership on my home folder (i own it)
4: erased .gnome .gnome2 .gconf .gconfd .metacity
5: purged gdm and reinstalled
6: created a new user with admin privileges and a new home folder        
7: tried booting with later kernels

none of them helped.

well...  i think that's it. can't think of more...

---

### Post by BigT0 on 2009-07-11
i was thinking and i said "lets try logging in from shell then bring up X"
so at the login screen i dropped to shell by ctrl+alt+f2.
put my username and password and i logged in.
ran "sudo killall gdm"
then "startx"
i see that it loads up to "/usr/bin/X11/X"
then i see....

```
Saw signal 11. Server aborting
 ddxSigGiveup: closing log
 ddxSigGiveup: re-raising 11
xinit: connection to X server lost.

waiting for X server to shut down
```

and that's it. back to CLI

---

### Post by BigT0 on 2009-07-11
well..... 
i got it fixed..
it wasn't a gnome problem after all.
it was something with acpi.
got it fixed with this....

[http://ubuntuforums.org/showthread.php?t=767668](http://ubuntuforums.org/showthread.php?t=767668) 

2nd post.

thanks anyway!!

---

