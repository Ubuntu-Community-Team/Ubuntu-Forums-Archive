---
title: "Lost X after libGL error"
date: 2006-10-05
forum: Desktop Environments
---

### Post by LittleLebowski on 2006-10-05
After much frustration involving the common libGL.so.1 error and my attempts to use Amarok and Mplayer, I tried symlinking libGL.so.1 to libGL.so.1.2 which didn't work.  I then tried unisntalling a whole bunch of apps and lost X completely.  Reinstalled xserver-xorg and ran dpk-reconfigure xserver-xorg.  Start X works for a moment and then crashes with the error at the end of the log reading "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.  Running startX as a user (only works as root) gives me the error "X: unable to open wrapper config file /etc/X11/XWrapper.config  X: user not authorized to run the X server, aborting."

  I am sure I can fix this and recover my desktop and hopefully even fix the libGL error.  This is on a Lenovo/IBM Thinkpad Z60 with an ATI video card.  
 
  I aprpeciate any help or ideas offered.

---

### Post by LittleLebowski on 2006-10-05
Any ideas?

---

### Post by LittleLebowski on 2006-10-05
I've tried reinstalling xorg and reconfiguring xserver-xorg.  apt-get dist-upgrade to no effect.

---

### Post by erikringmar on 2006-10-10
Hi there,

I have the same problem.  Any one out there?

---

### Post by LittleLebowski on 2006-10-10
I gave up and backed up and reinstalled.  Pathetic that so many people are having this sort of problem and there's no fix.  Sorry I couldn't help you.

---

