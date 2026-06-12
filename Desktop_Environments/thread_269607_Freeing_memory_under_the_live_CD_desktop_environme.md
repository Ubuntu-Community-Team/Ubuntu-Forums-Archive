---
title: "Freeing memory under the live CD desktop environment"
date: 2006-10-02
forum: Desktop Environments
---

### Post by K.Mandla on 2006-10-02
This is kind of a weird question. I've been working with a laptop without a hard drive, and setting it up as [an FTP server with the live CD]("http://www.ubuntuforums.org/showthread.php?t=268121"). Everything works great, except for one thing, and it's not related to servers, really.

If I boot the Xubuntu live CD and add the system monitor so I can see how much memory is taken up, it shows roughly 107Mb in use, out of 256Mb. Fair enough. That's about right. 

However, if I open a terminal and type *free -m*, I get only 34Mb free, with a huge amount lost to cache and buffers -- something like 155Mb.

And therein lies my problem. I don't really need an outlandish amount of space, but uploads to the server stop at 30Mb, and there doesn't seem to be any space available -- even if Xubuntu thinks there is.

I tried it on another machine with 512Mb, and in that case Xubuntu again reported only around 108Mb taken out of that 512Mb -- but *free -m* shows only 48Mb free, and uploads stop around 44Mb.

So what gives? It seems like Xubuntu doesn't allocate 128Mb or whatever to itself, but rather grabs something like 85 percent of the available memory and the rest is ... well, I don't know what it is.

How can I free up more memory? Is there a way to release the buffer and cache space?

I've tried "uninstalling" (via *apt-get remove --purge*) xubuntu-live and xuubntu-desktop, then *autoremove*ing everything that was orphaned. But for all I can tell this doesn't give any space back to the system. *free -m* shows the same results as before. ](*,) 

If anyone has any ideas for me, I'd be happy to hear them. :-k

---

