---
title: "wine + utorrent"
date: 2009-02-02
forum: General Help
---

### Post by diwas on 2009-02-02
The combination was perfect! I love utorrent above any other bittorent clients. But now it doesn't work. I have the latest WINE and the latest utorrent. 

When I start downloading after 5 minutes (approx) there's an error "Error: Request Not Supported"

This did not happen before, but now this happens everytime. 

I tried Deluge it doesn't have selective download. Ktorrent it has what i needed but everytime says "Failed to write on disk" even though my partition (NTFS) is working just fine. 
I want to use utorrent, it is perfect for me, but the error is pretty annoying.

Thank you.

---

### Post by halovivek on 2009-02-02
Try to change the port in utorrent and try again.

---

### Post by diwas on 2009-02-02
Thank you, 
I changed the port but still the problem persists.

---

### Post by halovivek on 2009-02-02
you can check more details help in this [thread]("http://ubuntuforums.org/showthread.php?t=191161")

---

### Post by swotie on 2009-02-02
why not use transmission bittorrent client, which is default in ubuntu ... it works perfect and is a super bittorrent client

---

### Post by Pidgin on 2009-02-02
Deluge supports selective download. The version in Ubuntu official repository is too old. Visit Deluge official site to get the latest version.

---

### Post by diwas on 2009-02-04
Thanks!!!!!!! Deluge supports selective download but there is a slight problem.
I was downloading Arch Linux from the official torrent, but deluge after a minute of downloading displays Error. And in the Details section there is a message saying "Status: Operation not Supported"...what might be the problem?

In windows with utorrent, the same torrent works just fine.

---

### Post by taurus on 2009-02-04
Just curious.  Where did you save the download files while using torrent clients in Ubuntu?

---

### Post by diwas on 2009-02-04
In my windows drive which is NTFS.

---

### Post by taurus on 2009-02-04
That could be the problem.  What if you try to save the download to your own $HOME?  Would it still give you that error message?

---

### Post by diwas on 2009-02-04
Oh! I havn't tested it.
But wait. I am downloading another movie and it doesnt show any error. So, is it my NTFS drive?

But one thing is for sure, Deluge is very very slow, in terms of download rate. Same torrent would download at 11, 12, 13, 14kbps...(around) but here deluge downloads at 1-7kbps..seldom reaching 11-14.

---

### Post by aibo99 on 2009-02-05
> **swotie said:**
> why not use transmission bittorrent client, which is default in ubuntu ... it works perfect and is a super bittorrent client

Transmission does not support DHT

---

### Post by diwas on 2009-02-05
I wish to know...what is DHT...in simple words please. 
And what about my problem?
> 
Oh! I havn't tested it.
But wait. I am downloading another movie and it doesnt show any error. So, is it my NTFS drive?

But one thing is for sure, Deluge is very very slow, in terms of download rate. Same torrent would download at 11, 12, 13, 14kbps...(around) but here deluge downloads at 1-7kbps..seldom reaching 11-14.

---

### Post by benzs_s on 2009-02-08
> **swotie said:**
> why not use transmission bittorrent client, which is default in ubuntu ... it works perfect and is a super bittorrent client

It's very, very buggy, like most lunix clients

---

### Post by diwas on 2009-02-08
I tested by downloading in the home folder but still Error is shown..:s

---

