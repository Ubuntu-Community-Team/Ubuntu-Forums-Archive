---
title: "LightScribe problem"
date: 2009-06-25
forum: General Help
---

### Post by bcg30506 on 2009-06-25
I'm running mythbuntu 9.04 and have installed the latest Lacie LightScribe software from this file on their site:

lightscribe-1.18.5.1-linux-2.6-intel.deb

and running the 4L program from:

[http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm]("http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm")

The program runs fine and detects my drive running the command:

gksudo 4L-gui

I was able to burn 2 disc labels.  Now I'm trying to burn a 3rd and 4th but it keeps telling me no media is detected in the drive.  The disc is in there and label side down.  It is from the same pack as the other 2 and using the same drive.  I've rebooted but still get the error.  I've tried another disc but the same problem occurs.  Has my drive (which is brand new) failed or is this a bad pack of discs?  Anyone got a suggestion as to what to try next?

```

$ sudo 4L-cli enumerate
Using /etc/lightscribe.rc
Drive path: /dev/sr0
Usable: 1
Full name: TSSTcorp CDDVDW SH-S223Q SB00 172
Model: CDDVDW SH-S223Q 
Manufacturer: TSSTcorp
Capabilities: monochrome 
Drive inner radius: 21700
Drive outer radius: 59000

$ sudo 4L-cli mediainfo /dev/sr0
Using /etc/lightscribe.rc
Media present: 0
Lightscribe media: 0
Oriented for labeling: 0

```

---

### Post by bcg30506 on 2009-06-25
Found a proposed answer here:

[http://www.lightscribe.com/discussionBoards/index.aspx?g=posts&t=2826]("http://www.lightscribe.com/discussionBoards/index.aspx?g=posts&t=2826")

that appears to be working (for now) as I'm burning a disc label using 4L-cli as I type this.  Time will tell.  Hopefully it was just a BIOS setting from building the machine, though I'm not sure how I got lucky on the 2 earlier discs that worked when using Lightscribe.

I changed the IDE configuration from RAID to AHCI instead.

---

