---
title: "Fusion .6 or Git on Gutsy"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by bobbob1016 on 2007-11-03
I've tried numerous scripts to get Fusion from git on Gusty, and I've even manually tried installing via git, with ./get-git, and I always get this error "make[3]: *** [window.moc.cpp] Error 127".

I want the git version because I read it has a lot of new features, and I want to try some plugins, namely the rotating windows like metisse or however it is spelled, and the 3D glasses one.  If anyone can help I'd appreciate it.

I've also posted in the compiz-fusion forums, but I thought to post here incase this Error 127 was a Gutsy issue, and not Fusion.  Thanks in advance.

---

### Post by DaveRM on 2007-11-04
bobbob-

Try the script at:

[http://telperion.wordpress.com/2007/10/27/fusion-nuovo-script-per-compilazione/]("http://telperion.wordpress.com/2007/10/27/fusion-nuovo-script-per-compilazione/")

The web page and some of the script is in Italian.

I used Google translate.

[http://www.google.com/translate_t]("http://www.google.com/translate_t")

Best part of the script is it can patch git with no-xcb.

A significant advantage because xcb and Sun jre  don't play nice together.

You must fill in the script with the type of installation you want.
There is also a restore routine in case of a bad git pull.

Give it a try.

DaveRM

---

