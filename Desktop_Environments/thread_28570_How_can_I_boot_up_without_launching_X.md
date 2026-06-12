---
title: "How can I boot up without launching X?"
date: 2005-04-20
forum: Desktop Environments
---

### Post by [censored] on 2005-04-20
How can I configure ubuntu to boot up in text mode, i.e, without launching X?

If you want to know my reason for doing this, it's because I'm interested in trying the standard nvidia drivers as downloaded from nvidia.com. I'm finding that my system seems to bottleneck when I play gl games or watch vids.  It's true that my system is only cutting edge technology circa 2001, but I never used to have that problem with mandrake, or even windoze.

---

### Post by cka on 2005-04-20
[QUOTE='[censored]']How can I configure ubuntu to boot up in text mode, i.e, without launching X?

If you want to know my reason for doing this, it's because I'm interested in trying the standard nvidia drivers as downloaded from nvidia.com. I'm finding that my system seems to bottleneck when I play gl games or watch vids.  It's true that my system is only cutting edge technology circa 2001, but I never used to have that problem with mandrake, or even windoze.[/QUOTE]
 I don't think there's any way you can boot up without X, but the next best thing is to ctrl+alt+F1 when you get to the GDM, login there and kill -9 the GDM from the console.  From there you can apt-get all the stuff you need to build the stock nvidia video module.

---

### Post by Alexander Kirillov on 2005-04-20
[QUOTE='[censored]']How can I configure ubuntu to boot up in text mode, i.e, without launching X?

If you want to know my reason for doing this, it's because I'm interested in trying the standard nvidia drivers as downloaded from nvidia.com. I'm finding that my system seems to bottleneck when I play gl games or watch vids.  It's true that my system is only cutting edge technology circa 2001, but I never used to have that problem with mandrake, or even windoze.[/QUOTE]
See this thread [http://ubuntuforums.org/showthread.php?t=28308](http://ubuntuforums.org/showthread.php?t=28308)

---

### Post by audax321 on 2005-04-21
[censored] if your only planning on doing this for the drivers, what i did is just put in an invalid video card driver in xorg.conf (like nodriv20123, or any other gibrish) and restart... when X goes to start it'll flash the screen a few times and give you an error saying it couldn't start and drop you to a console.... just make sure to do:

sudo nano /etc/X11/xorg.conf

to change the driver to nvidia after you install the nvidia driver in the console.

---

### Post by TravisNewman on 2005-04-21
update-rc.d -f gdm remove
replace gdm with kdm if you're using it. That's only a good idea if you want to have it do that every time. If you just want to do it temporarily, just kill gdm using 
/etc/init.d/gdm stop
install the drivers, and go

---

