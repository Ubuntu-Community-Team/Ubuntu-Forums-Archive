---
title: "Ibex will No Longer Boot"
date: 2009-03-23
forum: General Help
---

### Post by d2macken on 2009-03-23
Oh wise ones of the Ubuntu forum... I have to ask for your help!

A month or so ago, I installed Intrepid Ibex (via Wubi) on my girlfriend's troublesome Inspiron to land an OS that might be stable enough to make it through the rest of the University semester. Sure enough, everything has been great (although I haven't yet figured out how to safely move ibex to its own partition instead of this virtual wubi one). Anyway, we go out this afternoon and on our return, we her computer looked as though it had locked up, so we rebooted. However, when ubuntu was loading, we noted a failed indicator next to:

error while loading shared libraries: /usr/lib/libhal.so.1 Error 21

Strangely enough, it still asked her for her username and password... but no real graphical interface beyond the black and white of the command line. Now, when we boot, a blue screen pops up asking us what to do... either fix packages, try to fix xserver (hopefully this sounds familiar to some people). Anyhow, we've tried to work our way through all of the options, but we still haven't gotten anywhere. I'm not overly Linux savvy, so I was hoping some of the experts here might be able to shed some insight.

Greatly appreciated...

---

### Post by 123456789123456789123456 on 2009-03-23
I have never used the windows installer to install Ubuntu, I have allways downloaded the disk, and installed from the cd.  I have a copy of Ubuntu on cd, if you would like I can send it to you.

as far as I can tell, error 21 may be GRUB, linux boot loader, telling you it can't locate that file, or partition.

easiest way would be to use the live cd, locate the partition, get any data from it you want, and do a clean install.

---

### Post by James_Lochhead on 2009-03-23
Edit: Silly post. This is not a grub error.

21 : Selected disk does not exist. This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

---

### Post by James_Lochhead on 2009-03-23
Sounds like the hard disk might have died, or loose cables.

---

### Post by d2macken on 2009-03-24
Well, that's a scary diagnosis... BUT, the nugget of hope is that I am still able to boot Windows.

I also booted off the live disk, but my lack of experience means I have no idea what kind of diagnostics I should look for. Is there anything I could paste that might make this easier?

---

### Post by James_Lochhead on 2009-03-24
Ah... didn't read your whole post. Scratch that diagnosis. Should affect windows as well. I don't know much about Wubi tbh, so I really can't help you there.

---

### Post by bumanie on 2009-03-24
I don't know much about wubi either so I have no idea what the error means. There is a wubi specific posting area - may be you should ask one of the admins to shift the thread there. Being a wubi install, the problem could be related to fragmentation of NTFS, but that is only a guess. Alternatively, uninstall wubi via add/remove in windows and set up a dedicated ubuntu installation.

---

### Post by 123456789123456789123456 on 2009-03-24
You were able to start with the live cd.
under ubuntu live user session, live cd desktop, go to places menu
does it list both the ubuntu disk, and Windows disk, don't worry about names, there should be at least 2 disks listed. possible 3 with one being called swap.
the windows partiton may be identified as file system.
see if you can move to the other partiton, the one containing the copy of ubuntu
see if you can get the live cd to mount the drive.
That should tell us if the virtual partition is damaged in some way.
Super grub disk may be able to repair the GRUB part 1 on the MBR, that may salve the problem.

If not, I can walk you through a dual boot process using the live cd.

if you want to do that, I need to know what version of windows you are running.

---

