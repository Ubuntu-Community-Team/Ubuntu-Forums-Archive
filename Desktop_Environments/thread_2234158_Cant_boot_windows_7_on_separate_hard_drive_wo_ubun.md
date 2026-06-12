---
title: "Cant boot windows 7 on separate hard drive w/o ubuntu hard drive"
date: 2014-07-12
forum: Desktop Environments
---

### Post by jeffrey-hollis1 on 2014-07-12
I have 2 hard drivers

1 hard drive had windows 7 on it first.

Then I installed a 2nd hard drive and loaded 14.04 on it using usb.

Now when I remove the 2nd hard drive from the PC and boot it has a GRUB error.... cant find grub.

If i plug the 2nd hard drive back into the PC and boot is gives me the purple GRUB menu and I can select windows 7 and it loads with no problems.

How do I get windows 7 to just LOAD without having the second hard drive in the PC??

This is way over my head! 

Thanks to all of you in this community. Many would be lost without you all.

---

### Post by yancek on 2014-07-12
The default installation of the Ubuntu Grub bootloader is to the master boot record of the first drive.  In your case, that means it was installed to the windows drive.  You should install the Ubuntu Grub bootloader to the master boot record of the external (probably referred to as sdb if you only have two drives) with the command:  sudo grub-install /dev/sdb

To get windows installed to the mbr of its own disk, you can use the windows installation media to do that.  I'm not sure if this will work with a Recovery disk but it might.  Choose the Command Prompt option and type "bootrec.exe/fixmbr" without the quotes. Press enter.

---

### Post by oldfred on 2014-07-12
While you should always have a repairCD or live version of the current version of every system you have installed, you can install a Windows boot loader to the MBR of the Windows drive. Yancek's suggestion is probably better for the Windows fix as it installs the Windows boot loader.

With Boot-Repair it installs the syslinux boot loader which works just like the Windows boot loader. Do not use auto fix but in Advanced mode you choose each operating system and which drive you want boot loader installed into.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Grub also remembers where it installed. If it has remembered the hard drive that is Windows then you also need to update that setting otherwise on a major grub update it may just reinstall to sda and your boot from sdb will not then work as it is an old grub version.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
 or if UEFI system
sudo dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by jeffrey-hollis1 on 2014-07-13
I installed the grub on dev/sdb through root recovery after mounting. 

Said it was successful. 

I then (with ubuntu drive still installed) opened windows 7 cmd using live disk and entered your boot command. It said it was successful. 

I then removed ubuntu drive and hard reset pc from the open windows 7 cmd. 

I waited for boot load and I was still stuck at grub missing. 

Any other ideas?

edit: when I get to grub menu after boot it says windows 7 (loader) is on file path (on /dev/sda1)

Is that the file path I should use in root?

i can not get ubuntu to load because i installed nvidia driver update and get blank screen.

---

### Post by yancek on 2014-07-13
> I installed the grub on dev/sdb through root recovery after mounting. 

After doing that the next step would have been to reboot and change the boot priority to boot from sdb, the Ubuntu drive to see if it was successful.  If you were able to boot Ubuntu, you could then have run:  sudo update-grub.  It should have then detected windows on the other drive.  This would be handy if something happened to the windows drive, you could still boot it from the second drive.

 > I then (with ubuntu drive still installed) opened windows 7 cmd using  live disk and entered your boot command. It said it was successful. 

Do you mean:?  bootrec.exe/fixmbr?  I would have unplugged the external first.  Windows isn't going to recognize a Linux partition in any case.

> I then removed ubuntu drive and hard reset pc from the open windows 7 cmd. 

I would have just rebooted and then changed the boot priority to the windows drive to see if the windows boot repair command actually worked.

> edit: when I get to grub menu after boot it says windows 7 (loader) is on file path (on /dev/sda1)


Should be but, not necessarily depending upon the number of windows partitions.  You need to use the arrow key on your keyboard to highlight that windows entry, then hit the Enter key to see if it boots.

Did you try the second boot option for Ubuntu, recovery to see if it boots?

---

### Post by oldfred on 2014-07-13
Are you saying you do get to grub menu?
Then it has started to boot and probably is the video issue. Have you then tried second or recovery entry in grub menu? That auto adds the nomodeset boot option and removes quiet splash also.

---

