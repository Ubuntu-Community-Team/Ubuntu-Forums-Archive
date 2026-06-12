---
title: "after boot, usb keyboard isnt useable until os login"
date: 2008-05-12
forum: Desktop Environments
---

### Post by saphil on 2008-05-12
I have had this PC since 2003, running W2K Pro.  2 years ago, I dual-booted it with Win2k and Ubuntu because we had a user who got us the sony root-kit from an inborn need to listen to music on the pc, and I wanted to have an alternate OS to boot from if W2k became unusable again for some reason..  I set it to load to W2K automatically (on the os choices menu during start-up) as a grub option, rather than the standard Lunux-1st option.  I managed updates on both oses.  This worked great.  The Windows users never noticed that Ubuntu was there.  This year, the usual user of that machine threw away the ps/2 keyboard because it was really old and didn't work all that well.  Sometime later, I got the idea I wanted to boot the Ubuntu side and update it.  What I discovered is that the new USB keyboard's input is readable during boot, when one can choose to go to bios set-up, but becomes unreadable by grub, during the stretch when the os choosing menu is visible.  It works fine when Windows has reached its login screen.  I am thinking it might be something I could edit in the grub menu, since that is the control when the keyboard is not responsive, but it could be that the BIOS is old, and this is a message from the computer divas that I need to upgrade the hardware to a newer thing.  It is a whitebox machine, that I had built for me, rather than a name-brand.  I can likely dig up the details about the box if it would help answer the question.  I could also probably search around for a ps/2 keyboard and play with the Ubu side, then put it away for a year or so until the compulsion comes over me again...

---

### Post by retrow on 2008-05-12
I had a similar problem once when I tried a booting on an old timer Dell machine. I could hit F2 to enter the BIOS setup, but once grub took over, there was no use of the keyboard until either Ubuntu or Windows got loaded. 

Using a PS/2 keyboard solved the problem in my case. I recommend that option.

---

