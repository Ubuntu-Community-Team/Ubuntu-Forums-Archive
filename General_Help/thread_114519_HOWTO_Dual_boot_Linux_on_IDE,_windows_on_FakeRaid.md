---
title: "HOWTO: Dual boot Linux on IDE, windows on FakeRaid"
date: 2006-01-08
forum: General Help
---

### Post by defuseme2k on 2006-01-08
HOWTO:  Linux on an ide disk, windows on fakeraid dual boot.

Ok so I've looked everywhere and I couldn't seem to find how to dual boot when linux was the OS on the ide disk, and windows was on the fakeraid.  I'm personally trying to get used to linux and maybe later I'll move it to be the primary OS on my machine.  Using the linux boot sector only works when the windows and linux partitions are on the same disk.  Using that method we can make it work however... see below!

First use your windows system to create an NTFS partition on the ide disk, not very big 2 gigs is nothing, but I suggest this size for now, you can always use Partition magic or something later to shrink it, but on today's disks, really.. what is 2 gb?  Then shut down, remove the sata drives from the raid controller (in my case nvraid, and you don't have to unplug them.. but I suggest it).  Turn your pc back on and setup Linux on /dev/hda2, in my case Kubuntu and you must do an 'expert' install to be able to tell Grub or lilo (however I suggest grub :)) into /dev/hda2 NOT /dev/hda which would be the MBR.  Let the setup finish and just for now make sure it works.  (if you have the garbled display on reboot, use the recovery mode, login as root and use nano to edit the xorg.conf and set the nv driver to "vesa").  Once its proven to work, move on...

Next, restart the computer and make sure the windows xp setup cd is in your cdrom drive.  Set up windows and use the ntfs partition you created earlier, it will whine about needing to set the partition to active blah blah, go ahead and tell it to do what it has to and let setup finish.  We're not going to keep this install of windows, but once it finishes up reboot it and make sure it works, I would suggest rebooting it a couple of times.  Once this works move on..

Now that you have windows working we can do the HARD work =\.  Shut down your computer again, plug back in the sata raid set, and make sure in your bios before it boots up that your raid controller is first in line in the boot order.  Windows should boot properly from the raid.  Take this time to go ahead and delete the windows, documents and settings, and program files folders from the ide disk.  Then you will need a utility, just google for it, its called bootpart.  Extract bootpart anywhere, and then open up a command prompt and navigate to its folder.  Type bootpart and press enter at the command line and it will show you a list of partitions with a number to the left.  You want the linux partition that root is on.  So type bootpart x linux.lnx  at the command prompt, where x corrponds to the number that is the partition that the linux root is on.  Then using windows explorer, copy linux.lnx (or what ever you named it, I named mine kubuntu.lnx) to the root of the ide disk's ntfs partition.  This next part can be tricky if you're not super familiar with windows.  The easiest way is to make sure that you can view all files and folders, hidden or not, in the folder options.  Navigate to the root of the ide drive's ntfs partition and right click boot.ini select properties and remove the read only check mark, click ok, and then open this file with notepad (you should put it back to read only once you're done.. but don't have to).  At the Bottom type c:\linux.lnx="Linux" and save it. (in case you're wondering the ide drive will be c: in a minute) You should also edit the windows string as well.  Here is my boot.ini from the ide disk:

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="1. Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\kubuntu.lnx="2. Kubuntu Linux"

Its this line - multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect - that you want to edit (you should reflect these changes to the default= line as well if you plan on using windows as the deafult OS).  You can try it a few different ways but most likely you will just need to change yours to like mine is.  Notice the (0)'s and (1)'s follwoing the multi disk rdisk etc, these reflect where the bootable hard disk is in your system.  By default drive c:, partition 1, is all (0)s with partition set to 1.  Since you will be booting from the ide's mbr, you will need to change rdisk (most likely) to match the position.  From my experience (I'm not 100%) but I believe its based on your boot order in the bios.  You can also change default= to be in front of your linux bootsector file as well, thus booting to it by default if the time out expires.

Restart your computer, go into the bios before it gets restarted, and change the boot order to show the ide disk as the first hard disk.  You should get the boot menu with a 30 second time out (or what ever you set it to in boot.ini) allowing you to choose between linux and windows, choose linux to test that it boots up correctly.  If it does, you should be golden.  However you need to make sure windows still boots up, if it does not, you will have to go back into the bios, and flip the boot order back around, and once windows gets started edit the boot.ini again to test out another path for windows.

NOTE: to resize the partitions later on, you can use partition magic, however, you will need to recreate the bootsector file from the linux partition with bootpart and then place it in the root of the ide disk's ntfs partition.

I hope this made sense :).  If I made some kind of a mistake, or there is an easier way feel free to correct me.  Bottom line is there needs to be more information on how to do this type of setup, and I aim to help people is all :)

---

### Post by Indroth on 2006-07-06
There is a way to do this using GRUB which I found a little easier:

I installed windows on the fake RAID (nvraid) drives first, like you would if that was the only OS. Then I switched  the primary drive in my bios, and installed Ubuntu on that drive (again, nothing  special). Once the system could boot into linux, I installed dmraid, and set it up so the fake RAID volume shows up in /dev/mapper/...

The problem now is that GRUB doesn't know about dmraid... so I followed these instructions pretty much as is **starting from the step titled 'create initrd image'**:

[http://www.mepislovers-wiki.org/index.php?title=Fakeraid_mirror](http://www.mepislovers-wiki.org/index.php?title=Fakeraid_mirror)

The primary difference is that menu.lst now contains the following to load windows:

title             Windows XP
rootnoverify  (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader   +1

And that's it!

I suspect some of the mkinitramfs steps are unnecessary, but I only had a hazy idea of what I was doing there, so I don't know for sure.

---

### Post by brunom9 on 2006-10-16
Have a question....

Has anyone tried to install ubuntu and XP on the fakeraid? I'm trying to get it to work, so far I get an Error 12 on the boot sequence for windows XP right after the "makeactive" command... Don't know if it has something to do with the fact that XP is setup on an extended partition, will try again.

Also, what's the use of the "map (hd0) (hd1)" command?

Ok, will keep at it, will post if succesful.

Bruno

Otro amante del open-source en Mexico.
Another open-source user in Mexico.

---

