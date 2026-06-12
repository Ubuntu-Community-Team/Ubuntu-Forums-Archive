---
title: "How do I create a partition for windows?"
date: 2009-05-02
forum: General Help
---

### Post by mrzubi on 2009-05-02
Hello all,

Could someone please direct me to the easist way to set up a partition for a windows 7 installation?

I am currently running Ubuntu 9.04 with no partitions. What sort of steps would I need to take to be able to install windows 7 on my machine?

For a dual boot.. I just want to be cool. Im not leaving ubuntu : ) Its just for the video games.

---

### Post by mrzubi on 2009-05-02
Hello all,

Could someone please direct me to the easist way to set up a partition for a windows 7 installation?

I am currently running Ubuntu 9.04 with no partitions. What sort of steps would I need to take to be able to install windows 7 on my machine?

For a dual boot.. I just want to be cool. Im not leaving ubuntu : ) Its just for the video games.

---

### Post by Locutus_of_Borg on 2009-05-02
if you have free space, just create a new primary partition there

if not, you will have to resize existing partitions.  this can be done easiestly by using a livecd, opening terminal, and running 'sudo gparted'

if you cannot use a livecd, you can also do it from within your install on the terminal, as long as you have a partition you can unmount, e.g. something other than root

if you only have the one root partition and cannot use a livecd, it can still be done, but i am not going to explain how as it is both on google, and not necessary if you just boot off a live cd

after you create some unpartitioned space, windows 7 needs about 10GB and needs to be on a primary partition, and needs to already be formatted to ntfs, after that its really simple form the windows cd

---

### Post by pastalavista on 2009-05-02
I'm not sure you can. Windows needs to be on the first primary partition. It has always been recommended that, for a dual boot system, Windows should be installed first.

---

### Post by Locutus_of_Borg on 2009-05-02
it can be done

it doesnt need to be first partition, but it does need to be primary
you dont have to install windows first, but you will need to reinstall grub/lilo or configure windows bootloader to boot linux afterwards
and you do need already format the partition as the windows 7 installer will not do that for you or will not find the space

---

### Post by GolemdX on 2009-05-02
OK, you can't be running ubuntu with no partitions, because ubuntu is on a partition itself, and it requires another partition for swap space. What you can do is, download GParted from the web (you can't use it from inside ubuntu as for resizing the partition it would need to be unmounted), burn it, and boot from the disc. Resize the partition so you have as much unallocated space as you want for Windows. Run the Windows installer, and choose to install at the free space. Let it install.

Once it completes, GRUB should not be functioning. This link
[http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/)
shows how to repair the MBR.

This is the way it happened on the computer right next to me, and it's working great!

---

### Post by jerrrys on 2009-05-03
i use gparted to do this...it works fine, but some have said that its too slow...

---

### Post by caljohnsmith on 2009-05-03
Mrzubi, please observe the forum rules and do not start duplicate threads of the same subject/problem; that way those who help you will not be duplicating each others' efforts. I've merged your two duplicate threads into this one.

Regards,
John

---

### Post by finlost on 2009-06-27
I have been happily running Ubuntu 8.04 for about a year, but I failed to make any additional partitions upon installation other than the default ones created by the Live/installation CD (I believe I have the root partition and then two very small partitions).  I would like to poke around with Windows 7 RC to run a few apps that are not Linux compatible (QuickBooks and iTunes).

So let me get this straight....

I need to run the 8.04 Live CD where I can create partitions by running GParted in Terminal.  I create another partition where I can later install Windows 7 RC.  Does this impact my current install of Ubuntu 8.04 other than creating a new partition?  I am assuming a Live CD is needed because I cannot unmount my root partition within the Ubuntu OS.

Once a new partition is created, how does GRUB work?  More specifically, how do I then get my computer to know to install Windows 7 RC on the newly created partition.  I see a GRUB option upon boot up, but I haven't poked around with it. Do I use GRUB to switch to the new partition and then throw my Windows 7 RC disk in the DVD drive?

I see the link to fix GRUB in case it gets hosed up by Windows.  Does GRUB allow me to assign Windows as the primary partition as noted in this thread?  If not, where do I tell it to make the Windows partition the primary partition?

I am sure these are very basic questions, but I am very green to Linux as to what is behind the GUI.

---

### Post by Zaopunk on 2011-01-06
> **finlost said:**
> I have been happily running Ubuntu 8.04 for about a year, but I failed to make any additional partitions upon installation other than the default ones created by the Live/installation CD (I believe I have the root partition and then two very small partitions).  I would like to poke around with Windows 7 RC to run a few apps that are not Linux compatible (QuickBooks and iTunes).

So let me get this straight....

I need to run the 8.04 Live CD where I can create partitions by running GParted in Terminal.  I create another partition where I can later install Windows 7 RC.  Does this impact my current install of Ubuntu 8.04 other than creating a new partition?  I am assuming a Live CD is needed because I cannot unmount my root partition within the Ubuntu OS.

Once a new partition is created, how does GRUB work?  More specifically, how do I then get my computer to know to install Windows 7 RC on the newly created partition.  I see a GRUB option upon boot up, but I haven't poked around with it. Do I use GRUB to switch to the new partition and then throw my Windows 7 RC disk in the DVD drive?

I see the link to fix GRUB in case it gets hosed up by Windows.  Does GRUB allow me to assign Windows as the primary partition as noted in this thread?  If not, where do I tell it to make the Windows partition the primary partition?

I am sure these are very basic questions, but I am very green to Linux as to what is behind the GUI.

I am having this same trouble trying to install Win7 onto my Toshiba laptop. I get an error code 5 when trying to boot from the disk. So I shrank my ubuntu partition, reformatted the rest of the drive to NTFS and I am still unable to do the install (while in linux) due to the "there is no space for Windows to install" type error. 

Is there something I can do (as I am taking Ubuntu off the machine to sell it) to get Windows 7 to take?

Thank you.

---

### Post by Mark Phelps on 2011-01-06
> **Zaopunk said:**
> Is there something I can do (as I am taking Ubuntu off the machine to sell it) to get Windows 7 to take?

As you are planning on selling this, you need to remove all traces of Ubuntu, so keeping the old partitions is a mistake.

Boot into an Ubuntu LiveCD, open the Partition Editor, confirm that NONE of the partitions are mounted -- and remove ALL of the partitions.

Then, when you reboot with the Win7 DVD, you should be able to install with no problems.

---

