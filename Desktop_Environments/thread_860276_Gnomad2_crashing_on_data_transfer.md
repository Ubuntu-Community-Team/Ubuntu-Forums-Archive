---
title: "Gnomad2 crashing on data transfer"
date: 2008-07-15
forum: Desktop Environments
---

### Post by another_teajay on 2008-07-15
Hi, I searched some around this forum for threads about my problem, but without success. I using Gnomad2 in order to move directories from my Creative zen xtra 30gb to my computer.

I boot up gnomad, it takes a couple of minutes before all data is scanned, and then I kick off. I go to the data tab and select the first folder to be transferred - with the option to transfer all the subdirectories with it. Then here goes, the transfer dialog comes up and at this point gnomad dies.
I've tried running it as root, but that didn't work either.

Any help much appreciated!

---

### Post by another_teajay on 2008-07-15
seems like a known bug - segfault after all stuff in one directory is transferred. it wouldn't be so much of a trouble if the program load would be a little faster than the 5 minute load. Imagine about 1000 directories with files - if I had known this beforehand I would've archived all the backup. :(

---

### Post by daemonfly on 2008-07-20
I'm getting the same, but it's always only on certain files, if you watch which ones, then skip those, it should do the rest fine. Well...

I'm assuming it's either a problem with the tags or the encoding of the mp3s, so if you encoded or tagged the mp3s all with the same program, then you might have a problem with all the mp3s on the player.

The version of Gnomad2 Ubuntu has available actually is pretty old, it's behind a few versions. The gnomad2 site has the newer versions  in tar.gz format, and you have to manually make & compile them.

I haven't had a chance to try it out, as I'm at work, and I can't connect my laptop to the work network (laptop has gnomad2).

Edit: check this thread - [http://ubuntuforums.org/showthread.php?t=695381](http://ubuntuforums.org/showthread.php?t=695381)

edit #2: after manually downloading all dependancy packages to usb drive, and finally installing it on the laptop, the newest version, 2.9.1, still crashes on the "bugged" mp3 files with a seg fault. :(

---

