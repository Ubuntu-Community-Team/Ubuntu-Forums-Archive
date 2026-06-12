---
title: "Unity crash? when (re)starting network"
date: 2013-01-25
forum: Desktop Environments
---

### Post by yrm on 2013-01-25
Hi,

The problem is that when i try to (re)start my network from the terminal all the unity stuff disappears and i get a error:
Classic Guest Session has closed..
img: [http://tinypic.com/view.php?pic=200czsp&s=6](http://tinypic.com/view.php?pic=200czsp&s=6)

All window content stays in place but the window(close bar, borders etc) disappears and so does all the other unity stuff. 
Only the mouse works i can click but the keyboard does not seem to do anything.
So i press the reset button..

i use the following command to (re)start my network:
```
sudo service networking (re)start
```

it is a fresh Ubuntu 12.10 64bit install (the same happens when starting as live cd)

Im running this on a ivy bridge Z77 motherboard with a i7 3770k.
It might be worth mentioning that the onboard intel graphics are not recognized as it just says: driver unknown

Maybe i just overlooked something stupidly simple (i hope!) than please scream and shout at me how stupid i am!
Or if anyone could point me to a fix or the right direction to continue my search I'll buy you a beer!

thanks anyway! ):P

---

### Post by froman125 on 2013-02-13
I am having this problem as well

---

### Post by grahammechanical on 2013-02-14
First, may I say that if this is the error message

> Classic Guest Session has closed..

then Unity has not crashed because Unity is not being used. I would guess that it is the Classic session that has crashed, in particular, the Guest session.

Second, "Driver Unknown" as well as "Graphic experience Standard" are failings (bugs) in the Details utilities that are only now beginning to be put right in 13.04 Raring Ringtail. Ignore them.

Third, why are you running this command? What are you trying to do? Why are you doing it in a guest session?

As a complete guess I would say that starting (or restarting) something that is already running is producing the crash. First, stop the service. Then start it.

Regards.

---

### Post by Armann on 2013-02-22
It crashes on my computer as well.
I can see that this bug is more then a year old.
Why hasn't this been fixed ?
I don't like the network-manager and don't use it.
I'm not running the command as Guest...

---

