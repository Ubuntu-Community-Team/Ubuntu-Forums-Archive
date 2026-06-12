---
title: "Splash Screen"
date: 2009-04-26
forum: Desktop Environments
---

### Post by CodyT07 on 2009-04-26
I pretty much have all variants of ubuntu installed except for Xubuntu. Cause of this, I have had strange issues with splash screens randomly chaninging and being funny sizes and weird things. Anyway, I tried defaulting it back to ubuntu studios but in the process I broke the link set by usplash-artwork.so. 
Anyone know how I can default the link it is set to back?

---

### Post by ljerabek on 2009-04-26
Since...

/etc/alternatives/usplash-artwork.so points to /usr/lib/usplash/usplash-theme-ubuntu.so
/usr/lib/usplash/usplash-artwork.so points to /etc/alternatives/usplash-artwork.so

To list all the splash themes to know which is symbolic vs physical
From the shell run: ls -altr /usr/lib/usplash/
total 576
lrwxrwxrwx   1 root root     36 2009-01-03 13:40 usplash-artwork.so -> /etc/alternatives/usplash-artwork.so
-rw-r--r--   1 root root 505268 2009-03-19 19:45 usplash-theme-ubuntu.so
drwxr-xr-x   2 root root   4096 2009-04-25 16:09 .
drwxr-xr-x 209 root root  69632 2009-04-25 17:28 ..

Notice usplash-theme-ubuntu.so does not have an -> so it's not a link. This is the one you want to have /etc/alternatives/usplash-artwork.so point to.

so in theory you just need to do the following as root
ln -s /usr/lib/usplash/{name of your theme}.so /etc/alternatives/usplash-artwork.so
ln -s /etc/alternatives/usplash-artwork.so /usr/lib/usplash/usplash-artwork.so

---

