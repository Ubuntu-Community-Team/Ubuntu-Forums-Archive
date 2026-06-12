---
title: "eth0 and eth1 not automatically installed on IBM eServer x135"
date: 2006-07-16
forum: Desktop Environments
---

### Post by gpeters on 2006-07-16
Been running Ubuntu since the late Hoary days... but I have never had a problem where it does not detect the network interfaces.  I don't even know where to start.  An ifconfig reveals  only the local loopback is present.  Any thoughts on where I should start?  This is the first time I have tried Ubuntu on this web server.

---

### Post by mogelhead on 2006-07-17
Try the ["Wired Ethernet Troubleshooting Process"]("http://ubuntuforums.org/showthread.php?t=87643") guide on this forum. It is written for Breezy Badger 5.10 Release, but should work for Dapper as well.

---

### Post by gpeters on 2006-07-18
Thanks, but I followed everything on the guide.  I even installed 5.10 and it detected the eth0 and eth1... but it still will not get online or even ping my router.  The hardware works under MS Server 2000...  I would rather sell this server before I put a Microsoft Server OS on it.  Pretty disappointed in Dapper.  I had all the same install problems that other people are having and it didnt install my network hardware- both onboard intel e100 based cards.  Anyhow, thanks for the reply.

-G

---

### Post by mogelhead on 2006-07-18
You have followed everything in that guide you say. But at which point does it fail? At which point do you not get the same result as the guide?

So you have two intel e100 card.
What result do you get from ```
lspci | grep Eth
```?

Is the kernel module for the card loaded?
```
lsmod | grep e100
```

---

### Post by gpeters on 2006-07-19
lspci | grep Eth
gives me this-
0000:00:0d:0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 0c)
0000:00:0e:0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 0c)


lsmod | grep e100
gives me this-
e100          32768  0
mii            5248  1 e100

I have no clue what it means, but trust me, I appreciate the help- I don't want to have to go to CentOS or something redhat based that I know will support this instantly.  I have aquired a taste for Ubuntu.

---

### Post by mogelhead on 2006-07-19
I searched the forum for "Ethernet+Pro+100" and came up with the following thread: [how to set up an internet connection in ubuntu 6.06?]("http://ubuntuforums.org/showthread.php?t=209070")

The thread states that there is a bug with the Intel pro 100 cards, and how to work around the bug. See post number 12 and 13 on the second page.

---

### Post by gpeters on 2006-07-20
Excellent!  I spent the majority of the night getting a backplane fixed on a poweredge, but I will try this tomorrow and let you know if it works on my setup.  Once again, many thanks!

---

### Post by gpeters on 2006-07-21
!!!!  linux noapic boot option worked for 6.06 also.  Thanks for your help.  The ubuntu community is definitely one better for having helpful people like you around.

---

### Post by mogelhead on 2006-07-21
Glad I can help you =)

Credits to ubuntu forum users Kilz in [this thread]("http://ubuntuforums.org/showthread.php?p=1214260") and kamsar in [this thread]("http://www.ubuntuforums.org/showthread.php?p=159853").

---

