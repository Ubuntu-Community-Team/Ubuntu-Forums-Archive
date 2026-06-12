---
title: "problem installing on Vaio AR-870"
date: 2008-12-13
forum: General Help
---

### Post by linuxgr on 2008-12-13
Hi everybody! I have successfully installed ubuntu on my Vaio ar-825e. But I am having a lot of problems installing to a friend's laptop, vaio ar-870. Here's the problem:

When using Windows, it shows that it has a 500GB hard drive, two partitions(9GB Recovery + Windows the rest of the space). When I boot the live cd and start the gparted, it shows 2 hard drives with no partitions in either(two 250GB drives, both unallocated space). Cfdisk says something like "partition ends after physical end of disk".

I used partition tools in Windows to shrink the Windows partition down to 100GB(from 400+GB). Then gparted showed 2 disks again, but it found the two partitions, marked as "unknown". I went ahead and created an extended partition with swap+ext3 and installed linux. On the first boot, grub showed error 5(partition table problem) and wouldn't boot.

Why is this happening? The BIOS shows 2 disks, 250GB each but Windows Computer Management ->Storage Devices show only 1 HDD, approx. 500GB.

Anybody has any idea? Sorry for the long post, couldn't describe it better with fewer words. Thanks.

---

### Post by caljohnsmith on 2008-12-13
It sounds like your friend's computer is configured for RAID. If he wants to keep it configured for RAID and still install Ubuntu, you could look at:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Or if you can figure out how to take it out of the RAID setup without breaking Vista, it sure would make installing Ubuntu a lot easier. Good luck and let me know how it goes.

---

### Post by linuxgr on 2008-12-13
Oh I did not consider such case at all!! thanks!! Any tips on how to remove RAID? I do not think he really needs it......

And is there going to be a problem with Windows if RAID is removed?


thanks

---

### Post by linuxgr on 2008-12-16
Finally, I just removed raid through the bios. Of course, I had to re-install vista but at least linux could now see the partitions.

That's the first time I encountered such thing though. I find it very stupid to make a fake raid. Anyway, problem solved.

Thanks again!!!!

---

### Post by tfy on 2008-12-16
oh , thank  you very much .

---

### Post by caljohnsmith on 2008-12-16
> **linuxgr said:**
> Finally, I just removed raid through the bios. Of course, I had to re-install vista but at least linux could now see the partitions.

That's the first time I encountered such thing though. I find it very stupid to make a fake raid. Anyway, problem solved.

Thanks again!!!!
Glad to hear you could disable RAID and install Ubuntu; for the benefit of others, can you please take a moment to explain exactly what you had to do in BIOS to disable your RAID? There have been at least a few other people in the forums who have been in a similar situation, so it would really help if you could share that info. Hope your friend enjoys his new Ubuntu install. :)

---

### Post by linuxgr on 2008-12-16
Of course, silly of me, that's the whole benefit of the community, right?

I do not guarantee this will work for all laptops, but it should work for any laptop which has more than one physical drive and the BIOS capability to make fake RAID.

**WARNING!!!!!: Back-up ALL your data and create recovery disks! Removing Raid will result in losing _ALL_ partitions, including the hidden recovery partition. **

[U]Removing RAID configuration from SONY VAIO VGN-AR870:
[/U]

When the laptop starts(and shows VAIO logo) press F2 to enter the BIOS.

On the tab "Advanced" , you will see a line "RAID configuration" with an option "HIDE". Highlight that and press enter to change it to "SHOW".

Go to "EXIT" and save your changes.

The computer will reboot, and right after the VAIO logo screen, it will show the RAID configuration for a very short period of time. Be ready to insert CONTROL+I(or other indicated command) to enter the RAID configuration.

On the menu, you will see some options and your hard drives. Select the option "Remove RAID configuration" and on the next screen select both disks by pressing SPACE and then ENTER.

After you finish that, you will see a black screen saying "No operating system". At this point, hold the "power" key down for a few seconds until the computer shuts down. Then restart it and use your recovery disks to install Windows. DO NOT select the REPAIR option, as there is nothing to repair. Instead, select the VAIO recovery center(I think that's how it's called, the last option) and then select complete system recovery.


_Note 1_: If your computer does not initiate the recovery disk, go to the bios again and change the boot order of your devices.

_Note 2_: The Windows installation will use your first hard drive, but will leave the second inactive. After you finish installation, go to Control Panel->Classic View-> Administrative Tools-> Computer Management -> storage devices.

There, you will see your disks. Your second disk will appear as "not activated" on the right and on the left you see its space. Right-click on the right(where it says not activated) and select activate, and then select "mbr" option. Then right-click on the left(where it shows the capacity) and select "create" or "format"(I don't quite remember)

[U]
Note 3[/U]: Install Windows first and then linux, if that's what you want to do. The opposite will result in messing up your linux installation and your master boot record.



Any problems, feel free to ask questions in this thread!!!

---

