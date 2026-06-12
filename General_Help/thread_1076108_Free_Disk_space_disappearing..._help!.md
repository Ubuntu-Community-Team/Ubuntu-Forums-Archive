---
title: "Free Disk space disappearing... help!"
date: 2009-02-21
forum: General Help
---

### Post by -nat- on 2009-02-21
Just starting a few days ago, the free disk space on my Ubuntu 8.10 partition has started to disappear randomly. I have tried doing *sudo apt-get clean, sudo apt-get autoclean* as well as removing packages that aren't required.

The free space increases for a short while, before dropping back down to under 30Mb (sometimes it even goes right down to 0 bytes free).

According to disk usage analyzer I should have around 250Mb free, which sounds about right (It's a small partition), but everything else says I have 0 bytes free. :( 

Any help will be greatly appreciated, as at the moment I am pretty much unable to do anything on Ubuntu. :cry:

---

### Post by chmbrs on 2009-02-21
try 

fsck command in terminal to check disk for errors.

you might have to run it as root sudo fsck

why did you make such a small partition anyway. you should make it at least 5 or 10 gb, i think

---

### Post by mb_webguy on 2009-02-21
DO NOT RUN FSCK ON A MOUNTED PARTITION!!!

If the "small partition" is a necessary one like root or home, then you need to boot from the LiveCD and use fsck from there.  But never, ever run fsck on a mounted partition!

---

### Post by -nat- on 2009-02-21
Thanks for the warning mb_webguy!
I ran fsck while booted from the liveCD and this was the result:
```
ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda3: clean, 159831/340032 files, 1287924/1355713 blocks
ubuntu@ubuntu:~$
```

I'm not sure what this means so could someone possibly explain it to me?

---

### Post by Axanon on 2009-02-21
I am new, and trying to understand linux, but I would like to know the reason you should not run fsck on a mounted partition? What are the implications. From a noob standpoint it seems relatively safe, I'm obviously wrong though. Please explain.

---

### Post by -nat- on 2009-02-22
Anybody out there that can help?
I love Ubuntu, but with this problem I can't really do anything.
Please help!

---

### Post by dcstar on 2009-02-22
> **-nat- said:**
> Just starting a few days ago, the free disk space on my Ubuntu 8.10 partition has started to disappear randomly. I have tried doing *sudo apt-get clean, sudo apt-get autoclean* as well as removing packages that aren't required.

The free space increases for a short while, before dropping back down to under 30Mb (sometimes it even goes right down to 0 bytes free).

According to disk usage analyzer I should have around 250Mb free, which sounds about right (It's a small partition), but everything else says I have 0 bytes free. :( 

Any help will be greatly appreciated, as at the moment I am pretty much unable to do anything on Ubuntu. :cry:

Check /var/log to see if you have big logfiles.

---

### Post by -nat- on 2009-02-22
> **dcstar said:**
> Check /var/log to see if you have big logfiles.

It's only 16.7Mb, none of the files in it seem too big (all under 5Mb).

---

### Post by forkhandles on 2010-02-03
Hi, I'm having what sounds like a similar problem. Did you find the cause of yours? Thanks, Keith

---

### Post by cjazz on 2010-02-03
Well, until someone comes up with a better idea, you might want to use the 'du' command. It gives information on disk usage. For instance, if you enter
```
du -h /var
```
from the commandline, it processes /var and each directory within and reports on disk usage. Using the same process on subdirectories, presumably you can zero in on the offending directory and find out what you need nto know.

Sometimes the information can be fairly long, so you might want to pipe it to less, in order to page up and down, as follows:
```
du -h /var | less
```

You can also use sort to arrange the information numerically.
```
du -h /var | sort -n | less
```
would sort the directories from least usage to greatest.

If you're not comfortable with the commandline, I'd suggest you navigate to Places > Computer and double-click on File System. Right click on each major directory and choose "Properties" at the bottom of the list. That should give you the total size of the directory's contents and at least get you started in tracking down where your disk space is going.

---

### Post by Legionairre on 2010-04-15
Hey!

I just ran across this problem myself and have since fixed it, hopefully permanently.  

Quick description:  Available disk space went from 98 gb to 0 in a matter a day or so.  I actually saw it decreasing and thought it was just my own personal usage.  When I tried to make space after I was notified that it was all gone it would seemingly just disappear.

On second restart (first didn't change anything) went into recovery mode and ran everything but mem test.  Worked!

Hope this helps.

---

