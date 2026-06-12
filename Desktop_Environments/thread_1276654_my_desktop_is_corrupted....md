---
title: "my desktop is corrupted..."
date: 2009-09-27
forum: Desktop Environments
---

### Post by mephist0pheles on 2009-09-27
so when i upgraded to karmic koala (alpha) and restarted my comp, something rather dreadful happened. it said something about my filesystem being corrupted, doing some sort of manual fsck or something, which froze and didn't really do anything, i don't think. 

now, my desktop is gone. it's completely blank. as in, it's not there...at all. if i move a minimized window around on it, it moves with slow, choppy movements. 

help, please :confused::sad:

---

### Post by jerrrys on 2009-09-27
1  maybe try running fsck yourself;  don't know that is done in karmic
[http://www.google.com/search?q=fsck+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=fsck+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

2  boot to safe-mode in grub and try the fix package and the try to fix X option.

3  TestDisk in synaptic.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

i have nothing to offer as far as karmic specify fix

---

### Post by QIII on 2009-09-27
You have encountered a frequent problem with Alpha 6, which is what I assume you installed.

I hope you backed up you important files, which is something you should do when you make changes.

Did you attempt to upgrade from Jaunty?

You should be careful with pre-release versions of any OS, unless you intend to be involved in testing.  An Alpha release is not even a Beta, which is itself not even a release candidate.

First:  Did you do backups?

Second:  If you didn't do backups DON'T use you machine until you have had a chance to use something like Photorec or TestDisk to recover your important files.

Third:  You may have to reinstall Jaunty unless you really want to deal with the trouble of testing an Alpha, which you should NOT do on a "production" or regular use computer.

Fourth:  The way I had to get Alpha 6 running on my machines was to reinstall Alpha 5 and do a dist-upgrade because the install disks for Alpha 6 released on September 17th could do no more than completely bork my test systems... giving me one of the errors you are encountering.  I'm not sure if the images have been updated yet.

---

### Post by yanceypd on 2009-09-27
If grub gives the options showing earlier versions try selecting one of those with recovery mode.  Sometimes playing with new stuff can eat a lot of time up.

---

