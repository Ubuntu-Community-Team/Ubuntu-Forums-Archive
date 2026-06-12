---
title: "trouble executing et-linux-2.60.x86.run (installing Enemy Territory 2.60)"
date: 2007-02-17
forum: Gaming &amp; Leisure
---

### Post by Mattsg on 2007-02-17
Hi, new to linux and ubuntu. i have xubuntu 6.10 edgy installed and updated. my hardware is nforce4 motherboard and 7600gt nvidia graphics card. everything seems to run good as far as the OS goes.. im getting to know it better and enjoying it.
but... trying to install some games... having trouble with ET.. looked through the forums, found several ways of doing the same things; executing the .run file.. either through bash, ./ , sh, su .... all come to an error that reads like this...

matthew@Matthew-Xubuntu:/tmp/et$ sudo ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
./setup.sh: 278: /home/matthew/.setup5825: not found
./setup.sh: 289: /home/matthew/.setup5825: not found

sometimes it cant find 3 files, sometimes 2.. 
as i said, im new to linux and trying my hardest to understand everything.. if you have any ideas, detailed answers would be appreciated!

thanks!

Matt

---

### Post by tonyisntcreative on 2007-04-20
I'm having this problem also, and only on Edgy!  Any help would be greatly appreciated.

---

### Post by hikaricore on 2007-04-20
I don't want to take the easy way out, but it's possible the download is corrupt?
Try downloading it again from a different mirror possibly.

I'm not saying this is the end all be all solution but I've encountered problems like this before and it was as simple as that.

---

### Post by lakersforce on 2007-04-21
I found the solution! Look here: [http://ubuntuforums.org/showthread.php?t=416871](http://ubuntuforums.org/showthread.php?t=416871)

---

### Post by lakersforce on 2007-04-21
> **Mattsg said:**
> Hi, new to linux and ubuntu. i have xubuntu 6.10 edgy installed and updated. my hardware is nforce4 motherboard and 7600gt nvidia graphics card. everything seems to run good as far as the OS goes.. im getting to know it better and enjoying it.
but... trying to install some games... having trouble with ET.. looked through the forums, found several ways of doing the same things; executing the .run file.. either through bash, ./ , sh, su .... all come to an error that reads like this...

matthew@Matthew-Xubuntu:/tmp/et$ sudo ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
./setup.sh: 278: /home/matthew/.setup5825: not found
./setup.sh: 289: /home/matthew/.setup5825: not found

sometimes it cant find 3 files, sometimes 2.. 
as i said, im new to linux and trying my hardest to understand everything.. if you have any ideas, detailed answers would be appreciated!

thanks!

Matt

If you really want to get to the gritty part of it, do a:
```
sh et-linux-2.60.x86.run --keep
```
You will still get the error messages, but the content of the file will be unpacked to a folder named "build-install-2.60", which should be in the same directory as your et-linux-2.60.x86.run file. Go into the folder, open up setup.sh in a text-editor and take a look on line 278 and 289.

---

