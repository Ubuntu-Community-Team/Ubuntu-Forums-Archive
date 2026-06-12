---
title: "how to improve log on time in jaunty?"
date: 2009-04-23
forum: General Help
---

### Post by weeman7007 on 2009-04-23
first things first... I absolutely love jaunty, have been using it for about a week now! It boots really fast (total loading time is about 15-20 seconds less for me now than on Ibex!! Good job folks!) but what seems to let the whole process down for me is the log on times, because getting to log on screen is fast but then logging in is fairly slow in comparison.

So, I was wondering what I could do in order to make it log in faster, any help is appreciated, thanks.

---

### Post by Peter09 on 2009-04-23
Check in 

System->Preferences->Startup Applications 

see if there is anything that you can remove.

---

### Post by weeman7007 on 2009-04-23
Thanks. I have disabled some, but others I'm not sure whether or not I should touch them..

I have:
AT-SPI registry wrapper (what does this do and can I disable it?)
avant-window-navigator (I like this cos its pretty)
conky1 and conky2 (I like these because it has two instances of conky one on left and one on right side
GNOME settings daemon (sounds important? can I disable?)
GNOME settings daemon helper (same as above)
Power manager (I have a laptop... but don't really use the battery, can I disable this?)
Print queue applet (I don't print much.. but if I disable this will i still be able to?)
update notifier (if I disable this will it still automatically check for updates?)

thanks for help, I also set the GRUB timeout to 0 secs instead of 3, because I only have ubuntu installed and so its not necessary as I don't use the other things as if something goes wrong I just reinstall.

---

### Post by minisori on 2009-04-23
If i don't remember bad, the bad login time is due to a race condition caused by compiz and other applications. So unless you disable compiz i doubt you are going to get better times.

Correct me if i'm wrong?

---

### Post by weeman7007 on 2009-04-24
I don't think I have compiz installed... unless its installed by default?

---

### Post by minisori on 2009-04-28
Yes, it is.

---

### Post by kpkeerthi on 2009-04-28
> **weeman7007 said:**
> I don't think I have compiz installed... unless its installed by default?

Compiz is installed by default. But it is not enabled unless System -> Preferrences -> Appearance -> Visual Effects is turned on.

---

### Post by kpkeerthi on 2009-04-28
> **weeman7007 said:**
> 
I have:
AT-SPI registry wrapper (what does this do and can I disable it?)

AT => [Assistive Technology]("http://packages.ubuntu.com/hardy/gnome/at-spi"). You may turn this off if you don't intend to use GNOME's accessibility features.

Also, look in System -> Admin -> Services. I have cups and bluetooth disabled as I don't need them.

---

