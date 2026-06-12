---
title: "Strange Problem"
date: 2006-08-30
forum: Desktop Environments
---

### Post by swmiller6 on 2006-08-30
```
swmiller6@swmiller6-laptop:~$ sudo rm /home/swmiller6/.mozilla/firefox/man05hiu-01.default/prefs.js
Password:
rm: remove write-protected weird file `/home/swmiller6/.mozilla/firefox/man05hiu-01.default/prefs.js'? y
rm: cannot remove `/home/swmiller6/.mozilla/firefox/man05hiu-01.default/prefs.js': Operation not permitted
swmiller6@swmiller6-laptop:~$

```

Anyone else having this problem? I really need to remove this file it is 4GB!!!!! happened after I followed this [http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper]("http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper").
I have tried many things to remove it including chown, chattr, sudo rm, and some other things I found via google. 
I have not been using Linux for very long so if you have a solution for me then please be specific when giving me instructions.. 
Here is a screen shot of the file permissions...
[IMG]http://trademarkclan.net/images/off_site_images/weird_file.png[/IMG]

swmiller6

---

### Post by rmjokers on 2006-08-30
Dont forget that you need write permissions on the directory containing the file in order to delete the file.  Make sure of that by running (sudo chown a+w "directory name").

Otherwise, it is possible that the file may somehow be locked by an application.  You could try rebooting with the live CD, mounting the filesystem and deleting it from there.

Any idea how the file got such strange permissions / ownership?

---

### Post by swmiller6 on 2006-08-30
> **rmjokers said:**
> Dont forget that you need write permissions on the directory containing the file in order to delete the file.  Make sure of that by running (sudo chown a+w "directory name").

Otherwise, it is possible that the file may somehow be locked by an application.  You could try rebooting with the live CD, mounting the filesystem and deleting it from there.

Any idea how the file got such strange permissions / ownership?

I have no Idea how I got this file... It happened right after following the wiki for ati xgl/compiz thing... Thanks for the quick reply I will try the live cd...

swmiller6

---

### Post by swmiller6 on 2006-08-30
It did not work.... This is really strange, the file permissions and ownership can not be changed... Ant more ideas? 
Could this be some kind of virus?

swmiller6

---

### Post by xtknight on 2006-08-30
Use a forceful remove with verbose.

sudo rm -vrf /home/swmiller6/.mozilla/firefox/man05hiu-01.default/prefs.js

Chances are your file system is corrupted.  Try using **fsck** from recovery mode.

---

### Post by swmiller6 on 2006-08-30
> **xtknight said:**
> Use a forceful remove with verbose.

sudo rm -vrf /home/swmiller6/.mozilla/firefox/man05hiu-01.default/prefs.js
```

swmiller6@swmiller6-laptop:~$ sudo rm -vrf /home/swmiller6/.mozilla/firefox/man05hiu-01.default/prefs.js
Password:
rm: cannot remove `/home/swmiller6/.mozilla/firefox/man05hiu-01.default/prefs.js': Operation not permitted

```
did not work..
> **xtknight said:**
> 
Chances are your file system is corrupted.  Try using **fsck** from recovery mode.
```
swmiller6@swmiller6-laptop:~$ sudo fsck
Password:
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda2 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?

```

How do I do this?



swmiller6

---

### Post by swmiller6 on 2006-08-30
Thanks guys...
Just thought I would let you know that runing fsck solved the problem.. For those who do not know how to fsck this is what I used to figure it out [http://www.ubuntuforums.org/showthread.php?t=124615]("http://www.ubuntuforums.org/showthread.php?t=124615") Still I wonder what could have caused the problem in the first place?

swmiller6

---

