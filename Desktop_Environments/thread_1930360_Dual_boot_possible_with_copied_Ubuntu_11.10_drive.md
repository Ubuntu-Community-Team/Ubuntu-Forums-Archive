---
title: "Dual boot possible with copied Ubuntu 11.10 drive"
date: 2012-02-23
forum: Desktop Environments
---

### Post by GarrettVD on 2012-02-23
[LEFT]Hi all,
So, I've done extensive Googling on the subect of dual booting between Ubuntu and Windows XP / 7.  Many presume that the reader is looking to have a fresh install of either Windows 7 OR Ubuntu.  However, my scenario is a bit different.

I have a Thinkpad with Windows 7 on one HDD.  I've swapped out the DVD drive with a SATA HD adapter so I can put Ubuntu on there.  Now, I currently have Ubunti 11.10 installed on my development box, so what I've done is clone the entirety of the dev. box HDD to the SATA drive, and put the drive in the expansion bay.

Now, I'm wondering how I can go about harmoniously dual booting between the two?

Any help would be greatly appreciated,

-G.
[/LEFT]

---

### Post by ajgreeny on 2012-02-23
Have you tried booting to the ubuntu disk by changing the boot priority in BIOS or using a key at power-on.

If you can get that to boot without a problem all you probably need to do next is open a terminal in ubuntu and run the command ```
sudo update-grub
```
The system should then add windows to the grub menu automatically, allowing you to boot windows from grub.

You will, of course, always need to boot to the ubuntu drive as first priority from then on.

If the ubuntu disk will not boot, can you tell us what happens when you try to do so with any error messages you see..

---

### Post by oldfred on 2012-02-23
Welcome to the forums.

Does BIOS let you boot from your expansion bay?

Did you install any proprietary drivers in you install? 

ajgreeny was quicker.:)

---

### Post by GarrettVD on 2012-02-23
Hi there,
Thanks for the prompt response.

I can select the boot drive from the BIOS, but when it attempts to boot from that drive, it's just a black screen.

---

### Post by oldfred on 2012-02-23
Can you also boot a liveCD or liveUSB?

Issue may be boot or after boot and a video issue. Different systems may need different video drivers.

Can you hold shift key from BIOS and get to a grub menu? If so try the nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by GarrettVD on 2012-02-23
> **oldfred said:**
> Can you also boot a liveCD or liveUSB?

Issue may be boot or after boot and a video issue. Different systems may need different video drivers.

Can you hold shift key from BIOS and get to a grub menu? If so try the nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Hi Fred,
I actually don't have GRUB installed on my Thinkpad -- It essentially just came with a pre-loaded image of Windows 7 on the primary HDD, and I've cloned the Ubuntu drive onto an ~500GB SATA drive, which I've plopped into the expansion bay on my Thinkpad.  I'm using the default BIOS bootloader to select which drive to boot from.  Is there a way to install GRUB2 without breaking anything?

Edit: AFAIK, LiveCD works fine

Thanks,

---

### Post by oldfred on 2012-02-23
You should be able to easily install the grub2 boot loader to the external drive with the liveCD. Or use Boot-Repair that you can download into the liveCd.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by GarrettVD on 2012-02-24
Thanks, Fred!  I will give that a shot in the morning and update this thread with my results! :)

---

### Post by GarrettVD on 2012-02-24
> **GarrettVD said:**
> Thanks, Fred!  I will give that a shot in the morning and update this thread with my results! :)

So the Boot Repair did the trick!  First, I did a check of the disk:
```
e2fsck -f /dev/sdc1
```

And then I installed boot repair, went through the grub repair process, and boom!  It worked!

Thanks!

---

### Post by oldfred on 2012-02-24
Boot-Repair seems to work for a lot of issues, Glad that worked.:smile:

---

