---
title: "Update causes partition error..."
date: 2007-06-02
forum: Dell  Ubuntu Support
---

### Post by lostinquestions on 2007-06-02
Nevermind, I'm stupid, already posted.

---

### Post by madmod on 2007-06-05
I think I may have had the same problem.  The Ubuntu dependencies might have been incomplete and the updates didn't settle in well at all.  My computer is the Dell Inspiron E1505n with 512MB RAM and it wouldn't start or recover after I'd received about 21 updates/upgrades.

Here's what I did:
1.  Start up and press F2 to go into the BIOS screen.
2.  Select the Boot option so you can make the CD-ROM player first in the boot order.  I think the HDD was
first on my computer out of the box.
3.  Put the Ubuntu 7.04 CD into the tray.
4.  Restart the computer.
5.  Ubuntu should start allowing you some options.  (I chose to do a total reformat and install of Ubuntu--skipping all the other partitions.  I wanted basically the partitions only needed by Ubuntu.)
You may want to keep the Dell partitions.  Anyway reinstall Ubuntu.  A clean install should fix things.
6.  Once Ubuntu has settled in, connect with an Ethernet cable and wait for the computer to dialog 
with the Ubuntu repositories for updates.  You should see approximately 50 updates/upgrades as of a few
days ago.
7.  Allow the updates/upgrades.  When you restart the computer, things should be okay.
At that point you should have a honey of a system.  Mine sure is.

---

