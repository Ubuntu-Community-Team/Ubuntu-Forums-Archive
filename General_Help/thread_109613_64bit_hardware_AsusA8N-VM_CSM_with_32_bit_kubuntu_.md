---
title: "64bit hardware Asus/A8N-VM CSM with 32 bit kubuntu 5.10"
date: 2005-12-29
forum: General Help
---

### Post by ttallos on 2005-12-29
I would like the stability of 32 bit. I want to know if you can load it on to a 64 bit Hardware setup. The motherboard in mind is  A8N-VM CSM? Is there any problem loading 32bit software on to 64bit. How bout that particular system board???Thanks.

---

### Post by fbg111 on 2006-01-26
No problem loading 32-bit Ubuntu onto 64bit A8N-VM CSM, as far as that goes.  However, no flavor of Linux yet fully supports this mobo, and getting the integrated video, networking, and sound to work on Linux is a challenge to say the least.  I just installed, so to speak, Ubuntu 5.10 (32b) on a diy pc with this mobo, after a night of trial and error.  I found I had to boot the install CD using the command line "linux noapic nolapic", otherwise it would hang on various operations on the SATA drives (starting the Partition tool, partitioning, writing packages to the partition).  Finally got it installed only to find that X wouldn't start, so I've got gui-less command-line access only.  More info and advice on getting it running with this mobo here:

[http://www.nvnews.net/vbulletin/showthread.php?t=57791&highlight=a8n-vm+csm]("http://www.nvnews.net/vbulletin/showthread.php?t=57791&highlight=a8n-vm+csm")
[http://www.nvnews.net/vbulletin/showthread.php?t=63378&highlight=a8n-vm+csm]("http://www.nvnews.net/vbulletin/showthread.php?t=63378&highlight=a8n-vm+csm")
[http://www.nvnews.net/vbulletin/showthread.php?t=60596&highlight=a8n-vm+csm]("http://www.nvnews.net/vbulletin/showthread.php?t=60596&highlight=a8n-vm+csm")
[http://www.nvnews.net/vbulletin/showthread.php?t=61350&highlight=a8n-vm+csm]("http://www.nvnews.net/vbulletin/showthread.php?t=61350&highlight=a8n-vm+csm")
[http://www.nvnews.net/vbulletin/showthread.php?t=61238&highlight=a8n-vm+csm]("http://www.nvnews.net/vbulletin/showthread.php?t=61238&highlight=a8n-vm+csm")
[http://www.nvnews.net/vbulletin/showthread.php?t=61001&highlight=a8n-vm+csm]("http://www.nvnews.net/vbulletin/showthread.php?t=61001&highlight=a8n-vm+csm")

(Search the nvnews.net forums for more threads, though these are the ones that mention the a8n-vm csm specifically in the thread title)

---

