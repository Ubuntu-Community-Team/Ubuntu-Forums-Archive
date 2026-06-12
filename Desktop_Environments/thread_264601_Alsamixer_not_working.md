---
title: "Alsamixer not working"
date: 2006-09-24
forum: Desktop Environments
---

### Post by mark2741 on 2006-09-24
I have been using Ubuntu for about 6 months now and love it with one exception - sound issues. I should just bite the bullet and ditch the Creative Soundblaster Extigy external sound unit that I use for sound as it is nothing but a  hassle, and get a soundblaster live card, but just haven't gotten around to it as I want to wait until I just buy a new computer with built-in sound (my sound needs are simple).

I've gotten sound to work for the most part fine however I just installed Wolfenstein: ET game and get no sound. Video works beautifully, but no sound. I've rebooted twice and still no luck.

I've tried: killall esd in the terminal, but no luck.

That used to solve flash problems I'd have sometimes (haven't had those issues in a long time though thankfully).

In searching previous posts on wolfenstein issues I keep finding posts advising people to check their alsamixer and that it is an OSS problem and that you should get rid of OSS. Well, I see alsamixer in my Applications menu but Ican't start it - I get an error. When I try to launch alsamixergui from the apps menu I get:

alsmixer: function snd_cntl_open failed for default: no such device

When I try to run it from the terminal I get:

mark@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
mark@ubuntu:~$

How do I fix this?

---

