---
title: "ATI (restric), Gutsy, Compiz and dualhead = not possible???"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by millfarm on 2007-10-30
Hi,

I'm running Gutsy on my HP Compaq nc6400 with an ATI Radeon card and I'm using the restricted ATI driver and after a lot of difficulties got the Composite extension to work, but after I got this working I can't enable dualhead, I can see that my external screen is active, but when I move my mouse to the right of my laptop it just appears as a cross...

Any ideas?

---

### Post by millfarm on 2007-10-30
come on... this is really annoying, does any one know?

---

### Post by mahehellraiser on 2007-10-30
how u eliminated tht composite extension thing?

---

### Post by millfarm on 2007-10-30
I changed the last part of my xorg.conf where it said 
Composite "0"
to 
Composite "1"

and the I ran this from a console:
sudo apt-get install xserver-xgl

and the ctrl+alt+backspace..
and that was it.

if this doesnt work for you, then try : [http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+gutsy+composite](http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+gutsy+composite)

---

