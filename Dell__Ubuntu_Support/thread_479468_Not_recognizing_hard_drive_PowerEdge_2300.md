---
title: "Not recognizing hard drive PowerEdge 2300"
date: 2007-06-20
forum: Dell  Ubuntu Support
---

### Post by johnveal on 2007-06-20
I get "No hard drive detected" after it starts the bootable cd.

Any idea?

I'm very new to Linux so please keep it simple.

---

### Post by Yoooder on 2007-06-21
Is there already any Operating System on the machine?  What happens if you try booting without the LiveCD?

fyi: A LiveCD (like the Ubuntu installation CD) generally ships with a Linux kernel that supports nearly all hardware, to make it compatible with a very broad range of PCs.  Going by this it makes it sound as though possibly a cable has come loose internally, or something else is up.

You can also check your BIOS (On a Dell I think you press F2 when the Dell logo shows up a few seconds after powering on the machine) and search around in there to see if it lists your harddrive under the Primary or Secondary IDE controllers or under a SATA controller.

If you can't find any drive references in your BIOS  you can try the Load Defaults option for the BIOS (just in case a setting got messed up) and see if that helps.

---

### Post by johnveal on 2007-06-21
There is an OS on the hard drive. If I boot without the CD it boots into Windows Server 2003.  I hoped that it would recognize that and ask me to format before the install.   I'm going to check the connections and re-seat the Hard drives.

---

