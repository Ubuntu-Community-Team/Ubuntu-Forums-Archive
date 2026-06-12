---
title: "UT2003 in Gutsy"
date: 2007-10-26
forum: Gaming &amp; Leisure
---

### Post by arizonagroovejet on 2007-10-26
This is just for anyone else having trouble installing Unreal Tournament 2003 under Gutsy to hopefully find.

You'll find that you can't get past the CD key verification. It will say that the CD keys do not match and also show an error message. (I can't remember what it was, something about [[[ 54 and the word expected IIRC, a shell script error message anyway.) If you have this problem then:

Delete the directory you installed in to. By default this is /usr/local/games/ut2003. Then do

```
$ cd /bin
$ sudo unlink sh
$ sudo ln -s bash sh
```

Now run the installer again and the CD key check should work.

If you have stuttering sound then find the UT2004 demo for Linux and install that. Then do
```

$ cd /usr/local/games/ut2003/System
$ sudo mv openal.so openal.so.orig
$ sudo cp /usr/local/games/ut2004demo/System/openal.so .
```

If you run Kubuntu then you'll get no sound it arts is running. Edit the K Menu entry for ut2003 so the Command field reads

```
skill artsd && /usr/local/games/ut2003/ut2003
```

---

### Post by MrFSL on 2007-12-21
> If you have stuttering sound then find the UT2004 demo for Linux and install that....

There is a patch which is not well publicised:
[http://0day.icculus.org/ut2003/ut2003lnx_patch2225-3-BETA.tar.bz2](http://0day.icculus.org/ut2003/ut2003lnx_patch2225-3-BETA.tar.bz2)

It fixed my Gutsy stuttering audio and much much more! It has never run so well in Linux yet!

---

