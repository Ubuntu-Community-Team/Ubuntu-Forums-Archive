---
title: "Idle....Then error"
date: 2009-05-10
forum: General Help
---

### Post by kamasabi on 2009-05-10
Hey ya'll,

I've come across an annoying little problem that seems to have presented itself recently.  I have my old machine set up as a file server, and it will start up just fine and dandy without issue.  Then, after a while, it just does some random stuff and it ceases to work.  Samba stops working (but the machine is still pingable), trying to browse any directories says "Could not open file:///", no application is registered as handling this file".  Or when I try to open terminal, it says "Could not launch terminal".  Failed to execute child process "gnome-terminal" (Input/Output Error).  Unfortunately this will happen over and over and I have no idea why. 

Any ideas?

EDIT:  Running 9.04, replaced a defective hard drive and was running 7.10 before)
EDIT2:  On shutdown, it says 
[3798.698202] end request:  I/O error, dev sdb, sector 41141263
[3798.698339] end request:  I/O error, dev sdb, sector 41141263
[3798.860056] end request:  I/O error, dev sdb, sector 71024911

---

### Post by ciaovos on 2009-05-31
I get the same exact input output error.  My fear is that my drive is going bad, but I still am holding out hope there is a solution out there.

Do you have a raid configuration?  If so - in your bios, do you have raid autodect/ahci enabled or raid autodect/ata enabled?

---

### Post by kamasabi on 2009-06-04
Turned out the drive itself was bad.......it was not in a RAID configuration.  Honestly I don't know about the other part you were asking, I needed to build a new file server anyway so I did that.

---

