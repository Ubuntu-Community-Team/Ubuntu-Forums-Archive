---
title: "Problems with Boot Loader  Cant Find Files"
date: 2009-02-28
forum: General Help
---

### Post by PlatosGimp on 2009-02-28
I have a system running a 3ware raid card, and an external eSata connected rive. The boot loaded on /dev/sda is from OpenSuse, which boots fine. Under OpenSuse the partiton that Ubuntu got installed on is /dev/sdb9, but I beleive when Ubuntu was installed, the devices were different.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6              89G   23G   62G  28% /
udev                  2.0G  1.4M  2.0G   1% /dev
/dev/sdb3              99M   51M   43M  55% /boot
/dev/sda5             112G   80G   32G  72% /mnt/Windows/Removable
/dev/sdc1             298G  147G  152G  50% /mnt/Windows/Data
/dev/sdb7              87G  5.4G   77G   7% /mnt/Linux/Fedora
/dev/sdb8              83G  2.2G   77G   3% /mnt/Linux/Kubuntu
/dev/sdb9              86G  2.8G   79G   4% /mnt/Linux/Ubuntu

I installed Ubuntu's boot loader on the Ubuntu partition /dev/sdb9, and the entries below are from the menu/lst under Ubuntu. Which I added to the working bootloaded (OpenSuse). But cant seem to laod Ubuntu? Any suggestions? I have tried part7, part8, part9 ect in the entrie below


###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0 - 2.6.25.20-0.1 (default)
    root (hd0,2)
    kernel /vmlinuz-2.6.25.20-0.1-default root=/dev/disk/by-id/scsi-1AMCC_9QM47LY300000500B54E-part6 splash=silent showopts vga=0x346
    initrd /initrd-2.6.25.20-0.1-default

###Don't change this comment - YaST2 identifier: Original name: linux-2.6.25.20-0.1-pae###
title openSUSE 11.0 - 2.6.25.20-0.1 (pae)
    root (hd0,2)
    kernel /vmlinuz-2.6.25.20-0.1-pae root=/dev/disk/by-id/scsi-1AMCC_9QM47LY300000500B54E-part6 splash=silent showopts vga=0x346
    initrd /initrd-2.6.25.20-0.1-pae

###Don't change this comment - YaST2 identifier: Original name: xen###
title Xen -- openSUSE 11.0 - 2.6.25.20-0.1
    root (hd0,2)
    kernel /xen.gz 
    module /vmlinuz-2.6.25.20-0.1-xen root=/dev/disk/by-id/scsi-1AMCC_9QM47LY300000500B54E-part6 splash=silent showopts vga=0x346
    module /initrd-2.6.25.20-0.1-xen


title		Ubuntu 8.10, kernel 2.6.27-7-generic-Part8
uuid		28ea8698-88ac-4207-b9d0-5d39183ce740
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/disk/by-id/scsi-1AMCC_9QM47LY300000500B54E-part8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		28ea8698-88ac-4207-b9d0-5d39183ce740
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=28ea8698-88ac-4207-b9d0-5d39183ce740 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

---

### Post by thtrgremlin on 2009-03-01
I must first admit that I have never trieg booting from a raid before with ubuntu, but from much experience with grub and grub problems, two things look completly out of place in your ubuntu entries:
1) uuid
2) quiet

Just as a suggestion, since nobody else has posted a solution yet, rather than editing your /boot/grub/menu.lst, startup to grub, select the '
title Ubuntu 8.10, kernel 2.6.27-7-generic' entry, press 'e' to edit, and comment out the 'uuid' and 'quiet' lines, and see if it will start then. As mentioned before, never seem 'quiet' or quiet' as grub commands before. kernel options, yes, but not grub commands.

After you make the changes to each of those lines, just press 'b' to boot. It will use those settings just that one time, but doesn't change your config file. If that works, make the changes perminent in /boot/grub/menu.lst

Hope that helps. If that was unclear, I can repost clearer directions if any of that is unfamiliar.

Best luck.

---

### Post by -kg- on 2009-03-01
No, quiet is present in my menu.lst, as well.  One of my entries:

> title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-23-generic
quiet


Although my Recovery mode entries (the second entry) doesn't have it:

> title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro single
initrd		/boot/initrd.img-2.6.24-23-generic
(No quiet present here in entry)


Everything works and I am able to boot into everything.  Note, however, what is missing in your menu.lst entries:

> MINE:

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

YOURS:

title Ubuntu 8.10, kernel 2.6.27-7-generic-Part8
uuid 28ea8698-88ac-4207-b9d0-5d39183ce740
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/disk/by-id/scsi-1AMCC_9QM47LY300000500B54E-part8 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

The "-Part8" portion is not in my entry.  Of course, the Title entry is what is displayed in the GRUB boot menu (I think), so that may not be the issue.  You have no "root (hdx,x)" entry at all.  And I don't know what's happening with your "kernel" line, but it is not at all like mine.

Now, you say that this is from the menu.lst generated when you installed GRUB in the partition in which Ubuntu is installed...could it be that they might be different if you installed Ubuntu's GRUB in the MBR of your boot disk?  That's the only thing that I can think it might be.

Definitely, if you copied the lines into the OpenSUSE GRUB, I would think that you would need that "root" entry to point GRUB toward the proper partition in which the rest of GRUB resides (for your Ubuntu installation, that is).  That would seem (to me) to be the key to your problem.  Being installed in the partition in which the root resides, it would not need that entry, since it resides in that partition.

I don't know for sure...it's just a thought.

---

### Post by thtrgremlin on 2009-03-01
it is possible to specify a default root, just to mention, but that could also be the issue (that there is no root specified). MAYBE it should be > title Ubuntu 8.10, kernel 2.6.27-7-generic-Part8
[COLOR="DarkRed"]root=[/COLOR]uuid 28ea8698-88ac-4207-b9d0-5d39183ce740
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/disk/by-id/scsi-1AMCC_9QM47LY300000500B54E-part8 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet 

But just food for thought, technically being familiar with grub console, I don't see why you would need to specify root both below title and in the kernel options. once it is set in the kernel, it should also be set for init. Furtner, isn't it redundant to have both 'kernel ... quiet' and 'quiet' at the end, or are they different? does the second quiet suppress init.s/rcS output? Think I need to test for another project I am working on.

Something useful I have resorted to before is going into a grub console and typing in boot options manually. 'help' has a great guide, not to mention, best of all, TAB COMPLETION! Makes it really easy to make sure you got all those strange names right, and very quick and easy to mess around with various settings until it all works correctly... then hopefully you remember what you did when you actually bother to go back and edit menu.lst

---

### Post by caljohnsmith on 2009-03-01
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your desktop, and then do the following as **root user**, but replace <username> with your user name:
```
bash /home/[COLOR="Blue"]<username>[/COLOR]/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. That will help clarify your setup and hopefully what the solution to your booting problem might be.

---

