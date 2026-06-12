---
title: "Xdmx help, discussion: has anyone gotten it to work?"
date: 2009-03-06
forum: Desktop Environments
---

### Post by slyn4ice on 2009-03-06
Hey guys,

I have been looking for a way to find another use for a laptop I rarely use (but with a 17" screen) and I came across Xdmx. There is something called MaxiVista for windows, but despite the name it doesn't work on Vista (unless you do some trickery). So, I decided to try trusty Ubuntu. I have 8.10 on both laptops. I followed and read through all the tutorials and posts i could google but i am stuck. So, here is what i am doing - hopefully someone could help me out here.

*Laptops have screen resolutions 1280x800 (primary laptop), 1920x1600 (secondary).
*Both have NVidia cards.
*On both machines I use the NVidia drivers.
*On both machines xsessions is modified to remove the '-nolisten tcp' part.

1. I start gnome sessions on both laptops. 
2. From gnome terminals I start a bare X with twm on both laptops using 'startx /usr/bin/twm -- :1'.
3. From terminals in the twm sessions I do the following:
   -on the secondary machine
     - xhost +{ip of the primary}
   -on the primary machine
     - xhost +
     - startx /usr/bin/twm -- Xdmx :2 \
       -display :1
       -display {ip of secondary}:1
       -norender
       +xinerama

At this point I should get another twm session started on :2 which spans both screens. What I get is both screens flickering at the same time, and Xdmx terminating on the primary machine with 'xinit error 111' and 'xinit error 3 (no such process)'. Up to that point it seems like Xdmx finds both screens and reads the geometry - there are no errors. I can't give the complete log since i am writing this from work but i can include it if necessary.

I am a complete newbie with X, xinit, startx so any help is appreciated.

Thanks

---

### Post by Zombie13 on 2009-04-21
I just got it working today.  Here's how I do it:

1) login to both machines as 'Failsafe Terminal'
2) run xhost + (or xhost + <name or IP of controlling node>) on both machines
3) on the controlling node, run "startx `which gnome-session` -- Xdmx :1 -display <name or ip of display 1, i.e. 192.168.222.11:0> -display <name or ip of second machine.> +xinerama -noglxproxy -norender <whatever other options you want>

That works fine.  Gets gnome spanning both laptops.

The biggest hurdle I had to overcome was a segfault when it tried to start up.  The solution was to use the Xdmx package from Debian Etch.  The segfault issue is a documented bug and a fix is in progress, but it's not available as of the 9.04 repo currently. 

Loaded the Etch version and it worked nicely.

The problem I have now involves mixing 64-bit and 32-bit.  I have a 64-bit dual-core laptop that I want to use with an older, 32-bit P4 laptop, but I can't get it working.  Anyone have ideas on that?

Sorry for the long post, hope it helps someone.

Z.

---

