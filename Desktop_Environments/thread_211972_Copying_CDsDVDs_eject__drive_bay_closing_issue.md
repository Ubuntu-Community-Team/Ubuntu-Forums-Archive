---
title: "Copying CDs/DVDs eject / drive bay closing issue"
date: 2006-07-09
forum: Desktop Environments
---

### Post by edwing on 2006-07-09
Tried searching but couldn't find a solution... here goes my problem:

What I am doing is copying CDs and DVDs by right-clicking on the CD icon and selecting Copy CD/DVD. When the Copy process is done, it ejects and then almost immediately close the drive bay. Is this a bug or something I can configure?

---

### Post by RAOF on 2006-07-09
> **edwing said:**
> Tried searching but couldn't find a solution... here goes my problem:

What I am doing is copying CDs and DVDs by right-clicking on the CD icon and selecting Copy CD/DVD. When the Copy process is done, it ejects and then almost immediately close the drive bay. Is this a bug or something I can configure?
This is normal when the burner has finished writing a CD, if that's what you're talking about.  The CD drive needs to be told that the cd that used to be blank now has stuff on it, and so it should read it.  The easiest way to do this is to eject & reload the CD drive. :)

---

### Post by edwing on 2006-07-09
Yes but the drive bay closes too fast for me to take out the original CD and place a blank CD!

---

### Post by siccness on 2006-07-09
Try going to the command line, and typing:

eject /dev/hdc (hdc being a secondary master device)

---

