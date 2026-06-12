---
title: "Firefox problem"
date: 2005-10-14
forum: Desktop Environments
---

### Post by kirky3000 on 2005-10-14
I was doing my regular system update, but mozzila-firefox and mozzila-firefox-gnome-support both failed with this error:

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support

I have tried a few times to upgrade with the same results. 

But now firefox dosn't seem to want to start, if I start it from a terminal, I get no error and nothing happens.

Any Ideas waht I can do? 

cheers

---

### Post by TristanMike on 2005-10-14
I suspect [this is your problem](http://www.ubuntuforums.org/showthread.php?t=68294). Starting from comment 8 and continuing down. Make sure you have the correct backports too while your at it :)

---

### Post by kirky3000 on 2005-10-15
thanks for the help :)

---

