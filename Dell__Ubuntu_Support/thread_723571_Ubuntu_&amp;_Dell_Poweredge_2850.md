---
title: "Ubuntu &amp; Dell Poweredge 2850"
date: 2008-03-13
forum: Dell  Ubuntu Support
---

### Post by ubuntoexpert on 2008-03-13
My company are looking for a server to host a web service, and we have
been considering the Dell PowerEdge 2850 with:

- 2 x 64-bit Intel Xeon processor 3.4GHz with 2MB L2 cache and
- Integrated PERC4e/Di RAID Controller (RAID5)

We would like to run Ubuntu on it, but we would also accept pure Debian.

I have a couple of questions:

1. Will Ubuntu work with the Dell PowerEdge 2850
2. Does Ubuntu support Dells integrated SCSI controller: PERC4e ?

Thanks

---

### Post by pbcartwright on 2008-03-13
I've been putting Redhat on Dell poweredge servers for 2 years. The question isn't does dell support ubuntu, the question is does Dell support linux, and the answer is yes.

---

### Post by ubuntoexpert on 2008-03-15
> **pbcartwright said:**
> I've been putting Redhat on Dell poweredge servers for 2 years. The question isn't does dell support ubuntu, the question is does Dell support linux, and the answer is yes.
thank u

---

### Post by barichardson5727 on 2008-03-17
Yes, ubuntu already has the megaraid modules you will need to get your PERC 4e/Di running. The only functionality you will be missing from using ubuntu/debian over redhat would be the OMSA software; but you don't really need that unless you want to add or change your raid configuration from within the OS.

---

### Post by gtdaqua on 2008-03-19
> **barichardson5727 said:**
> Yes, ubuntu already has the megaraid modules you will need to get your PERC 4e/Di running. The only functionality you will be missing from using ubuntu/debian over redhat would be the OMSA software; but you don't really need that unless you want to add or change your raid configuration from within the OS.

but ubuntu's latest (gutsy 7.1 64-bit) ships with megaraid version driver 00.00.03.10-rc5 but dell requires 00.00.03.16. 
During Heavy I/O you may lose connectivity! 

Read [this]("http://ubuntuforums.org/showthread.php?t=722923") and [this too]("http://ubuntuforums.org/showthread.php?t=721342").

---

### Post by gtdaqua on 2008-03-19
This will also help (even though yours is PERC4e/Di), there could be reliability issues.

[How to make Ubuntu talk with Dell's PERC6?]("http://ubuntuforums.org/showthread.php?t=719556")

---

### Post by sr20ve on 2008-03-19
> **gtdaqua said:**
> This will also help (even though yours is PERC4e/Di), there could be reliability issues.

[How to make Ubuntu talk with Dell's PERC6?]("http://ubuntuforums.org/showthread.php?t=719556")

You're not going to run into any of those issues with the PERC 4, that you might with the PERC 5 or 6. The PERC 4 is a rock solid scsi raid controller, the PERC 5 and 6 is SAS/SATA and the drivers are still relativly new.

---

