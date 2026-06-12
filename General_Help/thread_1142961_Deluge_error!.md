---
title: "Deluge error!"
date: 2009-04-29
forum: General Help
---

### Post by diwas on 2009-04-29
This started happening in Intrepid and now I have Jaunty, it has again showing the same message. Basically, after some seconds of pressing "start" or "resume" this error message comes up. I have attached a screenshot showing this.

My target drive is NTFS, and yes I tried saving under / but still the problem persists.

In XP (same box) no problem is seen. So there must be something going on in Ubuntu which is creating this problem. I tried Ktorrent, but it cannot download as well.

I had posted another thread concerning same problem, but isn't much of a help there. Here's the link:
[http://ubuntuforums.org/showthread.php?t=1074541](http://ubuntuforums.org/showthread.php?t=1074541)


PS: I have posted this again because the other thread I posted had violated Forum code and Conduct.

---

### Post by diwas on 2009-05-01
bump

---

### Post by diwas on 2009-05-06
bump

---

### Post by bacardiandwatermelon on 2009-05-06
Sorry I can't be much help... Have you tried the latest version from GetDeb.net? [http://www.getdeb.net/search.php?search_distro_id=9&keywords=deluge]("http://www.getdeb.net/search.php?search_distro_id=9&keywords=deluge")

---

### Post by diwas on 2009-05-06
Thank you a lot for reply.
But yes, the latest version doesn't help. 
None of the torrent client works. Ktorrent, uTorrent, Transmission and Deluge. These are what I've tested. And unfortunately, none work :(

Due to this reason, I always have to switch to XP.

Hey! Is there any possibility that an un-configured VPN settings be the reason? Since the torrent stopped working, VPN settings was also damaged(haha i couldn't find another word!)

---

### Post by diwas on 2009-05-07
bump

---

### Post by diwas on 2009-05-08
bump

---

### Post by kk0sse54 on 2009-05-09
Have you set the proper permissions for your ntfs drive so that you have read/write access?

---

### Post by diwas on 2009-05-09
> **C!oud said:**
> Have you set the proper permissions for your ntfs drive so that you have read/write access?
Yes, I have. It doesn't work even if the target folder is inside /

---

### Post by diwas on 2009-05-09
Sorry for irrelevant data.

---

### Post by diwas on 2009-05-12
I tried using rtorrent, and it was working just great. But yet again, after few hours of download i get this error:

"File chunk write error: No such file or directory."

Now, what am I supposed to conclude from this? A quick google says that the torrent might be corrupt (since I did not install a new version and all) but i know the torrent isn't corrupt. Because the same torrent in XP is downloading without any problem.

Now, what must be going wrong here?

---

### Post by dubcee on 2010-11-12
Hey i'm not sure if this thread is still active at all... but i've recently switched to deluge and i get this error as well

Status: Operation not supported

As a work around, i've been downloading to my desktop and checking the box "Move Completed: ***". This has been working perfectly, but this is not ideal.

I'm trying to download to an NTFS hard drive, and i do have rwx access because it works with other torrent clients. 

**Using Deluge 1.3.1**

i'd love any help!

---

### Post by dubcee on 2010-11-14
bump!

---

### Post by dubcee on 2010-11-15
bump!

---

### Post by Cas07 on 2010-11-16
> **dubcee said:**
> Hey i'm not sure if this thread is still active at all... but i've recently switched to deluge and i get this error as well

Status: Operation not supported

As a work around, i've been downloading to my desktop and checking the box "Move Completed: ***". This has been working perfectly, but this is not ideal.

I'm trying to download to an NTFS hard drive, and i do have rwx access because it works with other torrent clients. 

**Using Deluge 1.3.1**

i'd love any help!

If you visit the official Deluge [fourms]("http://forum.deluge-torrent.org/viewforum.php?f=7") you will find more people to help. If you supply logs of the issue that would be ideal.

One thing to note that we do not recommend using NTFS with Deluge on Linux.

---

