---
title: "MP3 files play at lightning speed"
date: 2006-07-27
forum: Desktop Environments
---

### Post by pwaldo on 2006-07-27
Hi all,

I have sound working fine in KDE, and I can play .ogg files in amarok and juk.  When I try to play a .mp3, all players act as if they can play the files, but they speed through the music.  A 3 minute tune plays in about 2 seconds, and I get no sound.

I'm guessing that there is an mp3 package I need, but I am unaware of which one it is.  Any help would be greatly appreciated!

---

### Post by Lord Illidan on 2006-07-27
For amarok, you need libxine-extracodecs

---

### Post by Jucato on 2006-07-27
Just added info. the package *libxine-extracodecs* is found in the multiverse component of the ubuntu repository. You have to add/enable it in order to locate and install it. 

Good luck!

---

### Post by pwaldo on 2006-07-27
No joy in installing:

[FONT="Courier New"]pwaldo@office:~$ sudo apt-get install libxine-extracodecs
Reading package lists... Done
Building dependency tree... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate
[/FONT]

---

### Post by gingermark on 2006-07-27
do ```
kdesu kate /etc/apt/sources.list
``` then find the entries with "universe" in them, and add "multiverse" to those lines.

so, for example:
"deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe"
would become
"deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe multiverse".

Save the file, then do ```
sudo apt-get update
``` and try again. Should work now.

---

### Post by Jucato on 2006-07-27
Is the multiverse component of your ubuntu repository enabled? 

EDIT: just follow gingermark's tip

---

### Post by pwaldo on 2006-07-27
That did the trick!  I thought I had multiverse enabled, but it turns out it was only for dapper-backports.  Thanks!

---

