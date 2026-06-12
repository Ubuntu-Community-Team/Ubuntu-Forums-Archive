---
title: "Getting rid of the grubloader from Ubuntu"
date: 2006-01-16
forum: General Help
---

### Post by jrs1985 on 2006-01-16
I had to remove ubuntu for some reasons on my laptop (still on my desktop) I used to have the grubloader for ubuntu/windows xp dualboot. I used the ubuntu cd partition tool to get rid of the ubuntu partition, but now there's an error w/my grub loader. It says error 17 (I think) and now will not load anything at all. I need to get rid of this grub to automatically go to windows xp or something. Thanks

---

### Post by Qrk on 2006-01-16
Microsoft has a tool for this, fixmbr

Really, all you need to do is get into a windows recovery environment and type 

fixmbr 

into the command prompt.

Microsoft gives the guide.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)

---

### Post by inigmatus on 2006-01-16
or if you have a comp without a windows CD or boot disk: get on a friend's comp, google BootItNG, burn it to CD or copy to floppy, boot to BootItNG cd or floppy, don't install it, just go to partition worker or something like that, select the drive with windows partition, and hit "View MBR" and then hit the button "STD MBR" and it will do it all very effortlessly and painlessly. just reboot and take the cd/floppy out. windows should start normally.

if you want the standard instructions for using BootITNG to totally uninstall Ubuntu and Grub bootloader, go here: [http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)

---

