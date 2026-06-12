---
title: "Help on external"
date: 2009-04-16
forum: General Help
---

### Post by aafilmproductions on 2009-04-16
hey all of u i need help iim installing ubuntu as a second os to duel boot but i need to place it on an external drive how do i do this cuz when i install it it wants to partitio my computer harddrive????
plz help i need it

---

### Post by blazemore on 2009-04-16
go ahead and try for yourself if you want to put Ubuntu on an external HDD. There has been many searches on getting Ubuntu on an external HDD, so I&#8217;m posting this. I do warn you though, if you try this with your internal HDD in, you might damage it. Also, you will probably fail at this, just as a heads up. OK, now down to the instructions.

1. Format your external HDD to  ext3 or FAT32 or whatever you want it to be, it doesn&#8217;t matter as long as you wipe the hard drive clean.

2. Check your BIOS and make sure you are enabled to boot from an external USB device. (If you dont know what BIOS is then I highly recommend you don&#8217;t try this)

3. Put your copy of Ubuntu into the CD tray, turn off the computer, and remove your internal HDD. (If you leave it in very bad things will happen and you will lose everything).

4. Boot the computer from the CD and run a live session, make sure the external HDD is unplugged. (If you&#8217;re external HDD is plugged in at startup then the system will not boot)

5. Once it has booted, plug in the external HDD and wait for it to mount.

6. Click on the &#8220;Install&#8221; icon on the desktop, go through the language and time-zone steps, until the partitioner starts up.

7. Click on the second option that says &#8220;Guided - Use entire disk&#8221;. There should only be one drive that is found (sda), use it. If there is more than one drive in then exit the partitioner immediately, turn off the computer, and take out that other drive.

8. Partition the disk, it will unmount, but that is normal, go get a coffee or something because it will take longer than usual.

    NOTE: If you get an error installing GRUB or anything else then you have to restart the installation. This may happen sometimes due to the fact that you are using USB.

9. After the installation the CD will prompt you to reboot, restart the system, let it load, and voila!

---

