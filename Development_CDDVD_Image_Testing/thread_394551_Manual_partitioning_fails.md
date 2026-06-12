---
title: "Manual partitioning fails"
date: 2007-03-27
forum: Development CD/DVD Image Testing
---

### Post by rubenr999 on 2007-03-27
I saw this on the previous release too (daily/20070320.1/feisty-alternate-i386.iso).

I checked the md5sum and I burned a CD. I booted my pc and selected oem install. 

When I got to the menu of partitioning, I selected manual and after that, I reduced the size of the current partition ext3. Then when a display said that the next changes cannot be undone and I click ok, a message pop up saying "an error occurred while writing the changes to the storage devices, operation aborted". The same happened with guided resizing.

This bug was already reported, see #94647. cjwatson recommended to press alt-f2 in the installer after it fails, run 'e2fsck -f /dev/sda1' (or whatever the device name for the ext3 partition is), press alt-f1 after that finishes to get back to the installer, and then try the resize again. I will try this recipe and I will test partitioning again in the next release because it should be fixed since the beta.

---

