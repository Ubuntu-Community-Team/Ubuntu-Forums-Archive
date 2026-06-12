---
title: "running online.gnome.org under ubuntu gutsy"
date: 2007-11-15
forum: Desktop Effects &amp; Customization
---

### Post by bvidinli on 2007-11-15
get an online.gnome.org account.
login to your account.
click download.
your download link comes to your email.
click on link in your email.

download mugshot for fedora 7
save it to some location.
open console,
become superuser
write:
alien -i mugshot-1.1.45-1.fc7.i386.rpm --scripts

then,

ln -s /usr/lib/libpcre.so.3 /usr/lib/libpcre.so.0
ln -s /usr/lib/libpcreposix.so.3 /usr/lib/libpcreposix.so.0 

open your normal console, (non-superuser)
run mugshot... you should see your mugshot icon on your gnome panel...

have fun...

---

### Post by ghostcom97 on 2007-11-30
On my system i had to do this aswell to get mugshot to run:

```
sudo aptitude install libloudmouth1-0 libcurl4-dev
sudo ln -s /usr/lib/libcurl-gnutls.so.4 /usr/lib/libcurl.so.4
```

Haven't made any further testing beyond starting the app...

---

