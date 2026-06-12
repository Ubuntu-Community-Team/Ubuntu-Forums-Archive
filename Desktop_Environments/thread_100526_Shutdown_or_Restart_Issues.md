---
title: "Shutdown or Restart Issues"
date: 2005-12-07
forum: Desktop Environments
---

### Post by ctronics on 2005-12-07
I am a newbie to start off.  I really like linux, and want to move completly there.  I have two issues.  I will deal with them one at a time.  First one:

When I try to restart or shutdown everything seems to go okay until the final mesages.  I will post a few of them here to see if anyone can help.

Deactivating Swap....
unmount: tmpfs busy - remounted read-only                [ok]

Unmounting local filesystems......
unmount: tmpfs busy - remounted read-only                [ok]

Shutting down LVM Volume Groups...
[4302726.432000] ohci_hcd 0000:00:0f.2: bogus NDP=255, rereads as NDP=255

After that nothing happens, I have to manually reboot by hitting the reset switch or shut it down by holding the power button.  

I have searched and tried a few things.  I added the restart=h to the grub menu, and the restart worked only once.  

I do have a dual boot system, and the other system is windows xp.  They are on completly different hard drives.  The XP is on a SATA Drive, and my linux install is on the master IDE 1 cable.  

I hope that this is enough info to point me in the right direction.  I appreciate all of your help, and from what I see this is a great community to be a part of.  Hopefully I can get some good experience and be as productive as some I have seen.  Thanks is advance.  Please let me know if there is any more information that you need to help trouble shoot this issue.  After this is resolved I will deal with my graphics card issue which does not stop me from using the computer just stops me from playing Americas Army (my wife thinks that is a good thing....).

---

### Post by 23meg on 2005-12-08
I think you have an external USB storage device of some sort, right? Does the same thing happen when you unplug it?

---

### Post by ctronics on 2005-12-08
That was it.  I had 3 USB devices connected.  A USB Printer, a USB Digital Camera Docking station, and a USB flightstick.  I unplugged all three and it shutdown and restarted very smooth.  

I will play with them and figure out what one it is.  My guess would be the docking station.  

I really appreciate your help.  Now off to fix my printing issues.  Thanks again.

---

