---
title: "Restoring data to new partition table"
date: 2009-05-18
forum: General Help
---

### Post by Jesdisciple on 2009-05-18
I finally got the Live CD, booted on it, partitioned my HD (because what I did beforehand in fdisk didn't take certain things into account), installed, and everything was working fine.

Then I tried to restore my backed up /home data, but at first I extracted it at the wrong place (within /home).  I moved the archive to / and tried again; it worked partially.  I got several messages that no room was available in the device, peppered with others that said some of the data was successfully copied but not all.  I also noticed that I forgot to use the -p flag for tar, so I did it again to overwrite the files owned by root.  It still gave notices that the device was full.

I alloted 10 GB to /home; Nautilus said only 1.2 GB were used but that there was no remaining free space.  While I was restoring my data, I noticed two periods where Firefox wouldn't submit forms; the first one eventually ended (not sure why), but I tried restarting Firefox to fix the second.  That was a mistake; Firefox no longer had any profiles in its list because it had two profile folders named "default."  I couldn't merge the contents of the old into the new because the device was supposedly full.  I also could no longer use sudo; I got an error message about an invalid "MIT_MAGIC_COOKIE."

So I'm back on the Live CD, ready to repartition if necessary.  I can still access the installation if needed.  Please help!

---

