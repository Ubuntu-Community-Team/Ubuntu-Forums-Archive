---
title: "modprobe piix - tty job control error fix broken"
date: 2007-07-15
forum: Development CD/DVD Image Testing
---

### Post by mrbandersnatch on 2007-07-15
Installing Gutsy Tribe II on Asus G1S

Error when installing :
/bin/sh: can't access tty; job control turned off

I had this error on Fiesty (7.04) but was able to work around it by using "break=top" in the boot options and then adding "modprobe piix" when the command prompt came up and was able to boot and install.

In Tribe II this no longer works, resulting in a module not found error and thus it doesnt seem possible to install this release.

EDIT : I also had a quick look at the latest daily build and the same problem is evident here.

---

### Post by Krischi on 2007-07-17
I am getting a laptop just like this, and now you have me seriously concerned. 

I did some digging, and it looks as if this [kernel thread]("http://www.mail-archive.com/linux-ide%40vger.kernel.org/msg07416.html") talks about the same issues. It seems that a simple patch to the ata_piix driver is required to make it recognize the Santa Rosa PATA controller, and at this point all the problems might just go away.

Does anyone know what would be the easiest way to put and test this patch on the installation CD?

---

### Post by Krischi on 2007-07-18
Update: Gutsy can be installed via the alternate CD. Post-install, applying the patch 

```

--- drivers/ata/ata_piix.c.orig 2007-07-18 21:58:53.000000000 -0400
+++ drivers/ata/ata_piix.c      2007-07-12 11:27:49.000000000 -0400
@@ -201,6 +201,8 @@
        { 0x8086, 0x27DF, PCI_ANY_ID, PCI_ANY_ID, 0, 0, ich_pata_133 },
        { 0x8086, 0x269E, PCI_ANY_ID, PCI_ANY_ID, 0, 0, ich_pata_100 },
        { 0x8086, 0x811A, PCI_ANY_ID, PCI_ANY_ID, 0, 0, ich_pata_100 },
+       /* ICH8 Mobile PATA Controller */
+       { 0x8086, 0x2850, PCI_ANY_ID, PCI_ANY_ID, 0, 0, ich_pata_100 },

        /* NOTE: The following PCI ids must be kept in sync with the
         * list in drivers/pci/quirks.c.

```

to the Linux sources, recompiling the modules, and replacing ata_piix.ko with the patched version does the trick. After a modprobe ata_piix, the laptop can see the DVD drive.

This patch is already in the git snapshots, so it is only a matter of time until it propagates. Nevertheless, I will file a bug against the gutsy kernel.

Edit: You still need to put ata_piix in /etc/modules, but after that, the drive should hopefully be fully functional.

---

### Post by Yellowdog428 on 2007-07-19
Wow, i'm kind of new and I cant follow the above post ^-^  :confused:

Can someone else explain what I am supposed to do to fix this?  When I boot I get the same error
> Error when installing :
/bin/sh: can't access tty; job control turned off

To fix when I was running the live CD I needed to press F6 during boot and enter Break=Top then enter modprobe piix then enter.  Now that I have installed the break=top is not needed but I get the error while booting....

Hope I can get this thing solved.
Cheers

---

### Post by mrbandersnatch on 2007-07-19
Modprobe ata_piix works and let me install tribe III. I also needed to use modprobe ide_generic to get the CD visible.

Still have that damn tty job error on boot though and have to exit out of it *sigh*

---

### Post by iqiszero on 2008-05-28
Folks,
I think I have a great news to fix this **initramfs** issue.  Here is what I did.

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe ata_piix
modprobe ide_generic
exit

You will now boot into the LiveCD normally.  
Above worked successfully and I hope your case is working fine.

---

### Post by iqiszero on 2008-05-28
After you finish loading OS if you are able to open a terminal please do the following step 2).  If not (since it is asking restart) do step 1).

Step 1)
Reboot the system with LiveCD.
At the screen (Do not install, just boot the system w/o installation)
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe ata_piix
modprobe ide_generic
exit

2) Once you are in the system 
Open Terminal 
#mkdir target
#sudo mount /dev/hda1 target  (or whatever slie you installed)
#sudo chroot target

You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
You should do this with your favorite unix editor; or simply type the command:

#echo ata_piix >> /etc/initramfs-tools/modules
#echo ide_generic >> /etc/initramfs-tools/modules

After modifying the file you must update the system with the command

#update-initramfs -u
When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by ventrinal on 2008-05-30
Nice thread! I really like your provided information. It's really helpful for me.
Thanks a lot!

---

### Post by dhanusrav on 2012-12-11
> **iqiszero said:**
> Folks,
I think I have a great news to fix this **initramfs** issue.  Here is what I did.

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe ata_piix
modprobe ide_generic
exit

You will now boot into the LiveCD normally.  
Above worked successfully and I hope your case is working fine.
i did followed the 1st step but cant fix the sollution.. it loads for some time n showed the same ****... em so vexed, plz help me to solve this...

---

