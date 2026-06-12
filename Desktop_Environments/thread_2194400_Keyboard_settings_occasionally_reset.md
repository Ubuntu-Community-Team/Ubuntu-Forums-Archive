---
title: "Keyboard settings occasionally reset"
date: 2013-12-18
forum: Desktop Environments
---

### Post by pbean on 2013-12-18
Hi,

I'm experiencing a rather annoying problem using XFCE (on Xubuntu 13.10). Every once in a while, my keyboard settings simply reset. Things like the typing repeat rate and such, but also even my num lock status. My num lock light will stay turned on, but the functionality will actually be disabled (ie. the num pad works as arrow keys). Then when I press my num lock key, the light goes out, but the functionality is actually enabled (ie. the num pad works as numbers).

Both of these things are really annoying, since I often have to keep a button pressed (eg. arrow up) but because the repeat rate resets to something very slow, it suddenly goes all very slow. Also I have to type a lot of numbers, for which I use the num pad, but often it takes me entirely by surprise that the num lock status has reset.

I can't find any discernible reason for this reset whatsoever. It happens a couple of times a day, seemingly random.

What is interesting though, is when I go to the Keyboard settings in the Control panel, the displayed settings are still correct (ie. the keyboard repeat rate bar shows that it's supposed to be fast, like I set it to, even though the *actual* repeat rate is slow). If I just make a minor adjustment (eg. decrease the repeat rate by 1 and increase it by 1 again), all keyboard settings are all right again.

---

### Post by pbean on 2013-12-24
Bump. :-)

---

### Post by pbean on 2014-01-08
Sorry, but I will bump this yet another time. It's really annoying me, and really impeding my work day some days. :(

---

### Post by vasa1 on 2014-01-08
Can you try with another keyboard?

---

### Post by pbean on 2014-01-13
I tried with another keyboard, but the problems persist.

---

### Post by m-pricejones on 2014-04-07
I am experiencing this as well having recently updated my machine to Ubuntu 13.10 and installing xubuntu-desktop. Did you manage to track down a cause or find a fix?

---

### Post by pbean on 2014-06-06
Nope - still experiencing it to this day. :(

---

### Post by Toz on 2014-06-06
Is there a certain trigger that causes it? Suspend/resume perhaps?

When it happens, check to see if xfsettingsd is still running:
```
ps -ef | grep xfsettingsd
```
...and if not, try starting it up again.

You might also want to look at ~/.xsession-errors (if using a version prior to 14.04) or ~/.cache/upstart/startxfce4.log (if using 14.04) to see if there are any error messages that might help pinpoint the cause.

---

