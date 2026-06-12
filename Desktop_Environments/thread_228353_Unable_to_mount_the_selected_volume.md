---
title: "Unable to mount the selected volume"
date: 2006-08-03
forum: Desktop Environments
---

### Post by canucklehead on 2006-08-03
Hey guys, I'm extremely new to Ubuntu and experience a problem with my cd drive. This probably has a rediculously obvious answer but here goes:

When I open the cd tray and put a disc in, it opens back up. No error messages or anything. When I double click on CD-RW drive in Computer, it closes, then opens again with the message: 'Unable to mount the selected volume. <mount: no medium found>'

Any idea whats happening here? I don;t think its a hardware issue as the drive & disc both work fine on my Windows machines. Thanks,

---

### Post by carontis on 2006-08-03
Usually we check in the /etc/fstab file to see if everything is ok. Try this and see is your drive is already reported there, if not, you should add it. I send you also the copy of my fstab, so you can see how it is and if you need to add something. Remember that hdc is usually the name of 1st CDrom or DVDrom. To open your fstab for correction, you have to login as root and (I use *nano* editor) using a simple editor you can repair the all adding the simple line as is in my file. Hope it helps, if not, just let know.

=============================================================================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
============================================================================

---

### Post by wylfing on 2006-08-03
Canadian? Just guessing from the handle ;)

I am not too clear on what **carontis** is getting at. Looking into /etc/fstab is definitely an OK activity, but nothing you should have to worry about unless things are quite wrong.

Are you 100% positive about the disc you are inserting? What kind of disc is it -- DVD or CD? Are you sure your drive can handle the disc you are inserting? Generally, Linux is about equal to Windows for fault-tolerance of discs, but you should look at the disc and see if there are any major scratches, or if it needs to be cleaned. You can clean CDs and DVDs quite easily by swiping a clean cloth outward from the center of the disc to the edge, as if following the spoke of a wheel. (Never swipe circularly -- always from center to edge.) 

Let us know what is on that disc, and what type of disc it is, and what type of drive you have (detailed specs if you can provide them).

---

### Post by canucklehead on 2006-08-03
Ok thanks for your help, problem solved!

---

