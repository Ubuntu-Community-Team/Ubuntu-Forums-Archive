---
title: "tools to work with DNA sequence data"
date: 2006-10-14
forum: Education &amp; Science
---

### Post by machoo02 on 2006-10-14
Hi all,

Just curious if anyone has come across any good tools for manipulating DNA sequence data (e.g., viewing/editing .ab1 files, contig creation, etc).  During my Windows daze I used Bioedit ([http://www.mbio.ncsu.edu/BioEdit/bioedit.html](http://www.mbio.ncsu.edu/BioEdit/bioedit.html)) extensively, and although it works fairly well with WINE I'd like to find a native application.  Any ideas?

---

### Post by DrOlaf on 2006-10-16
If all you want to do is view a tracefile, I find the FinchTV viewer from [http://www.geospiza.com/finchtv/]("http://www.geospiza.com/finchtv/") to be pretty good. The linux binary works fine on my Dapper installation.

For more complex work, the only thing I have found is the good old Staden package. It has a learning curve like the North face of the Eiger, but it will do what you want. I have installed it from Sourceforge OK, but you may want to check out the Bio-Linux installation at [http://envgen.nox.ac.uk/biolinux.html]("http://envgen.nox.ac.uk/biolinux.html"). They have loads of bioinformatics software available. Don't let the website mislead you: they prefer to send you a DVD with a full distro containing enough software to set up a workstation, but as the programs are Debian packages they install pretty well under Ubuntu. Follow the instructions [here]("http://hocuspok.us/journal/bio-linux-bioinformatics-tools-for-linux") for details. There is also Phred/Phrap/Consed, but I'm still wrestling with installing that beast. 

Even if you get these installed, I'm afraid they don't have the functionality of some of the commercial packages, like Sequencher. But, as Sequencher is (a) not available for Linux, and (b) a dongle-protected app that costs $3,500 per license, I've had to make some sacrifices.

---

### Post by Lu-Tze on 2006-10-19
@ DrOlaf

Thanks for this information.  I did not know even know about these softwares.  I am still bouncing between Windows and Linux.  Mostly due to Windows-specific software requirements.  But these look great.  It even seems like Staden already does some of the stuff I had to write up in VB (not sure whether to put a :-) or a :-( ) because I could not find any reasonably priced software.  Have to try these out properly but so far Staden seems exactly what I need.

---

