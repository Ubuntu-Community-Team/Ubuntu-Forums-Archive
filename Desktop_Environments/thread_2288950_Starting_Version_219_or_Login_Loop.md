---
title: "Starting Version 219 or Login Loop"
date: 2015-07-30
forum: Desktop Environments
---

### Post by apfalzgraf8082 on 2015-07-30
Good evening,

I seem to be having some trouble with an Ubuntu 15.04 install.  I was using the fglrx drivers at one point, and I got stuck in a login loop that went unsolved (maybe you can help with that?).  I proceeded to remove the fglrx drivers from the recovery console (could not CTRL+ALT+F1 to a tty, it just showed a blank screen).  After removing and rebooting, I was stuck at a black screen printing Starting version 219 with a blinking cursor.  I have since reinstalled the fglrx drivers and am back at the login loop.  

I've tried several things (moving .Xauthority and generating a new one, reinstalling graphics drivers).  None of it appears to have worked, so I am looking for some general guidance.  I would appreciate any/all help.

Relevant System specs:
CPU: AMD FX 8320
GPU: AMD R9 280x

---

### Post by grahammechanical on 2015-07-31
What is the problem? is it the "starting version 219" message? or the login loop?

Ubuntu 15.04 was the first version of Ubuntu to use SystemD as the init system instead of Ubuntu's own init system called Upstart. The message is just a system message about the version of SystemD that is being used. That message will disappear when you upgrade to 15.10.

So, the problem to concentrate on is the login loop. And that is outside the area of my knowledge. Sorry.

P.S.

Assuming that there is nothing wrong with your password and assuming that you are using Ubuntu + Unity and that you can get to a console when at the login screen (Crtl+Alt+F1), then try these commands

```
sudo dconf reset -f /org/compiz
```

```
setsid unity
```

To get back to the login screen Ctrl+Alt+F7. 

Regards.

---

