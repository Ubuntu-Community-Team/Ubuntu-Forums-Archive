---
title: "Accidental hibernation messed up Ext2 IFS, please help!"
date: 2009-03-04
forum: General Help
---

### Post by lambda1729 on 2009-03-04
I've searched all over for this but all I can seem to find is people mentioning it as a problem and warning against it, not what to do if it happens.  If the solution exists somewhere else please point me in the right direction!

I'm running a dual-boot system with Ubuntu 8.04 and Windows XP Pro, each on its own partition, plus a home partition for my files (plus swap).  I accidentally hibernated Windows and subsequently booted into Linux.  There was some data corruption -- I lost some files -- and some errors the next few times I booted into Ubuntu which have since disappeared.  The lasting effect seems to be that the Ext2 IFS tool I installed on Windows in order to read my ext3 formatted home partition is no longer working and reinstalling it does not help.  (I know this is technically Windows software, but since it's specifically for reading Linux volumes, this seemed an appropriate place to ask about it -- if not please excuse; I'm pretty new to the Linux world.)

My questions:

1 - How do I get Ext2 IFS working again?  Do I need to reinstall both operating systems?  Please say no...

2 - Did I mess up anything else more fundamentally by doing this that I don't know about?  Is this a "reformat everything including the home partition" emergency, or are the corrupted files the extent of my screw-up here?

Please help!

---

