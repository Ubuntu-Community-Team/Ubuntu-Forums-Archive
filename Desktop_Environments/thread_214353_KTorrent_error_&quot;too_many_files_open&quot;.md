---
title: "KTorrent error: &quot;too many files open&quot;?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by themoebius on 2006-07-12
I'm trying to download a torrent of a large series of images and I get this error when starting the torrent:

Error starting torrent Images : Cannot open /home/zac/.kde/share/apps/ktorrent/tor0/cache/blahblah.jpg : Too many open files

this blah blah file is always the same one in the middle of the series. 
Everything in that cache directory is actually a link to the real file which I'm putting in /home/zac/Download/Images/blahblah.jpg. The link and the actual file exist, as do all the files before and after the one that I get the error on, but they're all 0 KB. I have pleanty of free space...

---

### Post by thegnark on 2006-07-12
sounds like there are too many file pointers open. i don't know what kind of limitations the kernel has, but it sounds like it's fvcking up your pr0n downloads

maybe this has something to do with not enough ram for all the file pointers?

i've personally never experienced the problem

---

### Post by themoebius on 2006-07-12
ya, its fvcking it up big time. I have 1.5GB of RAM, plus all that swap space so I doubt thats a problem... I'm using linux-image-2.6.15-26-amd64-generic, but I have a hard time believe the kernel is the problem either because I doubt it would be so limited in that respect and would I get a kernel panic or some kind of kernel error instead of a KDE error?

---

### Post by Jucato on 2006-07-12
I've encountered that problem, too, and I wasn't able to trace the cause. However, I just restarted KTorrent and the problem went away. If you haven't downloaded anything yet from that torrent, you could probably try to delete the tor0 folder (make sure KTorrent is not running) and restart KTorrent. Sometimes that works when I'm having errors with it.

---

### Post by Anduu on 2006-07-13
I know this little article is for Azureus however it explains why this happens under Linux and how to fix it.

[http://www.azureuswiki.com/index.php/Too_many_open_files](http://www.azureuswiki.com/index.php/Too_many_open_files)

---

### Post by themoebius on 2006-07-13
Ahh ok, that was it. Thanks!

---

