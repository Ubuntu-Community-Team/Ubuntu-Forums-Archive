---
title: "xf86config-4 Fatal Server Error: No Screens Found"
date: 2005-01-10
forum: General Help
---

### Post by FatChan on 2005-01-10
Hey guys,

I'm a total newbie and this is a great forum.  Ubuntu is my first go at linux and I've run into a problem.  AFter the initial installation everything was running great except I noticed that I could not set the resolution I wanted from the GNOME GUI.  I proceeded to try to edit the XF86Config-4 file to add the resolution that I wanted.  After much tinkering, not only have I failed to set my resolution, my XServer refuses to start.

When I type startx I get the following errors:

"Unable to find valid framebuffer device"
"NV(0): Failed to open frame buffer device..."
"Screen(s) found but none have usable configuration"

"Fatal Server Error:  no screens found"

I have tried to use the XF86config command, as well as 
dpkg -reconfigure xserver_xfree86

but XServer still refuses to start.  I need all the help I can get, thanks in advance.

---

### Post by echoi1975 on 2005-01-11
try X -configure and have X try to create a stub config file for you. 
if you can post your config file (minus the lines with comments (#)), we can take a look and see.

what kind of video card, video cable, monitor (lcd, crt, etc) are you using?

thx,

ec.

---

### Post by ups on 2005-01-22
Hi, I'm having the same problem. Google led me to this:

[http://lists.debian.org/debian-x/2002/10/msg00013.html](http://lists.debian.org/debian-x/2002/10/msg00013.html)

see the subsequent replies also. Seems disabling UseFBDev option can make it work. I haven't tried it yet, but will do it now.

---

### Post by ups on 2005-01-22
Alright, i tried it and it worked, posting from within ubuntu right now :)

Just open your /etc/X11/XF86Config-4 file
and then look in the Section "Device" for this line:
> Option		"UseFBDev"		"true"
add a # in front of it to comment it out:
> #Option		"UseFBDev"		"true"
Now it should work. Note that there might be some issues with games, as mentioned in the link above.

---

### Post by Compwiz on 2005-01-24
unfortunately this does not work for me ... it has some other errors: 

```
Failed to load module "v41" (module does not exist,0)
            no devices detected
             
            Fatal server error:
            no screens found

     XIO: Fatal IO error 104 (connection reset by peer) on Xserver ":0.0"
            after 0 requests - (0 known processed) with 0  events remaining

Xauth: (argv) : 1: bad display name "debian:0" in "remove" command
```

what exactly do these mean??

---

### Post by Compwiz on 2005-01-24
unfortunately this does not work for me ... it has some other errors: 

```
Failed to load module "v41" (module does not exist,0)
            no devices detected
             
            Fatal server error:
            no screens found

     XIO: Fatal IO error 104 (connection reset by peer) on Xserver ":0.0"
            after 0 requests - (0 known processed) with 0  events remaining

Xauth: (argv) : 1: bad display name "debian:0" in "remove" command
```

what exactly do these mean??

---

