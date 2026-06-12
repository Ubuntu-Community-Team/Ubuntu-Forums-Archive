---
title: "SEVERLY severly corrupt display! help me :("
date: 2007-06-29
forum: Desktop Environments
---

### Post by superyounan1 on 2007-06-29
** See the attached picture **

I was just logged on to my xgl session to show off compiz fusion to a friend but instead was greeted with a HORRENDOUSLY distorted screen. Except for the mouse pointer the screen wasn't readable or usable at ALL, but was still functioning. 

I went back to my regular session and took out compiz from the session startup and tried again, restarted a bunch of times, all didn't help.

Since the last time I used the xgl successfully, there were a number of software updates, including a kernal update.


[COLOR="Red"][UPDATE][/COLOR] I resolved this issue, hopefully this thread will help someone. 

The problem was with my video drivers - I use the ati fglrx drivers, and when the kernel update come through I had to reinstall my drivers. I followed manual installation methods found on the unofficial ATI linux wiki: [http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")

---

### Post by arvevans on 2007-06-29
I am seeing the same thing on my Ubuntu 7.04 64-bit OS on an AMD dual-core 64-bit system.  However, if I hit "CTRL-backspace" to kill the X session and spawn a new one, I can then log back in and things are fine for the rest of the time.  This just seems to happen occasionally after boot, but can be overcome by restarting X.
_._

---

### Post by needtolookatascreenshot on 2007-06-30
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

### Post by superyounan1 on 2007-06-30
maybe its a driver issue like i had, but i also saw on another thread that someone using kde had similar issues until they disabled transparency, maybe that applies to you

---

### Post by sjv123 on 2008-03-03
I have similarly corrupted display. I tried the CTRL backspace thing, but it opened some dialog  box that I cant read. :confused:

---

