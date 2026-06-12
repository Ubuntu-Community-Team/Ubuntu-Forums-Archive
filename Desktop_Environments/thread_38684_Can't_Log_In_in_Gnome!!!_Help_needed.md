---
title: "Can't Log In in Gnome!!! Help needed"
date: 2005-06-01
forum: Desktop Environments
---

### Post by PhoenixG on 2005-06-01
This is desperating, i really don't know what's happening. I can no longer log in in Gnome since when loggin in Gnome stays stuck in Metacity icon and can't progress until completing the log in. Sometime while stuck in metacity icon it starts repeating this icon may times in screen as if it was loading metacity many times... but never ends. The only way to log in is using Failsafe Gnome.  :mad: 
Could someone help me please? I'm starting to think that Ubuntu is not my distro cause It never happended to me on other distros. This is very strange.

---

### Post by thrift on 2005-06-01
Sounds like a config file got messed up.  The easiest way to fix that is to log in in safe mode, open a terminal, and then

ls -ha

find any .directorys(you'll see what i mean) that have anything to do with gnome or metacity in the name, and then delete them

rm -fR .directory1 .directory2 .directory3

THIS WILL REMOVE YOUR CONFIGURATION FOR THE PROGRAMS THAT STORE THEIR CONFIG HERE.

Once that is done try to log back out and in and see if it is fixed.

If you can't figure out what file it is, log in in safe mode, open a terminal and
rm -fR .*

this will remove your users entire configuration.

Log out and back in and if it still doesn't work, something is truely messed up on the system.

It is most likely that some application prematurely exited when writing to a config file.  This really doesn't matter what distro you are in, I've seen it happen in just about every distro I've ever used.  It can also happen when a newer version of a program reads an older config file and gets confused and things like this.

This shouldn't happen often, it's probably not Ubuntu's fault.

Hope this helps.

---

### Post by PhoenixG on 2005-06-01
Thank you very much. Your solution was OK, but instead of erasing directories I simply renamed ".gnome2" and found that this one was the faulty directory and now it is working properly again. Finally Ubuntu IS my distro.. I love it  \\:D/

---

