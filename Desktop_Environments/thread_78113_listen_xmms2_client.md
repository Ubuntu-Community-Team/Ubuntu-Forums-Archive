---
title: "listen xmms2 client"
date: 2005-10-17
forum: Desktop Environments
---

### Post by denkedran on 2005-10-17
I have two computers. Both running up to date breezy, with universe and multiverse enabled. I have also this ubuntu repository on both computers:
> deb [http://theli.free.fr/breezy/](http://theli.free.fr/breezy/) ./
This is for "xmms2" and pythonclient "listen".
when i start "listen" on the first computer it runs nicely. onthe second computer there is an error
> Traceback (most recent call last):
  File "listen.py", line 9, in ?
    import xmmsclient
ImportError: /usr/lib/python2.4/site-packages/xmmsclient.so: undefined symbol: xmmsc_medialib_playlists_list


some other infos:
first computer:
> -rw-r--r--  1 root root 51628 2005-09-15 20:27 /usr/lib/libxmmsclient.so.0
-rw-r--r--  1 root root 132464 2005-09-15 20:27 /usr/lib/python2.4/site-packages/xmmsclient.so

second computer:
exactly the same

---

### Post by ssam on 2005-11-08
did you ever solve this?

---

