---
title: "Problems displaying X apps from another server on my screen"
date: 2005-07-15
forum: Desktop Environments
---

### Post by timov on 2005-07-15
Today I swapped my Sun Blade Solaris 9 workstation for a smaller IBM server running Ubuntu 5.04. Most things I need to do for my work I can run with no problems so far, except when I try to fire up X applications on a server with my display exported to my workstation.

I've used the xhost + command on my Ubuntu box to allow all clients to connect.

I then log into one of my servers, do an export DISPLAY=ubuntubox:0.0 and try to fire up and X app (xterm for instance). 

They all give me the same vague error: 

xterm Xt error: Can't open display: XXX.XXX.XXX.XXX:0.0

(XXX.XXX.XXX.XXX being the correct ip for my new workstation.)

I tried setting DISPLAY as localhost:0.0 on my ubuntu box and I get the same problem. Also when I set my $DISPLAY back to normal (:0.0) on my Ubuntu box, I could run xterm onwe more, but I'm still having issues with a graphical installer (WSMclient for Linux from IBM).

Any one have an idea what it might be? 


thanx

Timo

---

### Post by timov on 2005-07-19
I've done some more digging about and found the problem. I need to change the start parameters of the X server to allow incomming conenctions. Currently it's running with the following parameters:

/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

I need to take out the -nolisten but can't seem to find where the options are stored/what start the X server with the options...


Any one who can point me in the right direction?

thanx

Timo


*edit*

Found /etc/gdm/gdm.conf and changed "DisallowTCP=true" to "DisallowTCP=false" and things work perfectly :)

problem solved.

---

### Post by patrick295767 on 2005-10-09
[QUOTE=timov]I've done some more digging about and found the problem. I need to change the start parameters of the X server to allow incomming conenctions. Currently it's running with the following parameters:

/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

I need to take out the -nolisten but can't seem to find where the options are stored/what start the X server with the options...


Any one who can point me in the right direction?

thanx

Timo


*edit*

Found /etc/gdm/gdm.conf and changed "DisallowTCP=true" to "DisallowTCP=false" and things work perfectly :)

problem solved.[/QUOTE]
  
  
   
  

I am not using gdm ... Is there a way without any gdm / xdm ... and so on ...
I start X only with startx ... 
Is there a way ??

Thank you very much !!

Pat'

---

