---
title: "How to add &quot;Other&quot; Linux distros on separate hard drive?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by ivanjs on 2005-11-03
Ubuntu is working great, it's dual booting with windows and that works great, but is there a way to add a hard drive that has another linux distro (fedora) to the GRUB menu to choose at bootup?

In other words, I want the fedora on  the new hard drive to show up in the grub menu created by ubuntu's installer so I can choose between ubuntu, fedora or windows.

Note that fedora is NOT a separate partition but a separate hard drive.
Thx.

---

### Post by Lambert on 2005-11-03
There is a way to do this. You have to edit grub.conf. I'm not the best to help you with this, maybe someone else can jump in with more experience.

You may want to look into installing a package called grubconf. It's a graphical frontend to editing grub. 

Otherwise try searching around the forums and google as you'll find there's a lot written on this. Mostly you'll see editing to dual boot into windows but the procedure is the same. You just need set grub correctly to point to the boot file for fedora.

---

### Post by rejser on 2005-11-03
have you already installed fedora? otherwise it's just to let fedora manage grub, it will recognize ubuntu and winblows

---

### Post by ivanjs on 2005-11-03
[QUOTE=rejser]have you already installed fedora? otherwise it's just to let fedora manage grub, it will recognize ubuntu and winblows[/QUOTE]

Yeah, I already have Fedora installed on the other drive.

---

### Post by ToastedToad on 2005-11-03
Here is what i would try:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

1. Install drive containing Fedora.
2. Boot into ubuntu, it should auto-detect the drive.
3. Navigate to the grub.conf file on the Fedora partition, it may be /boot/grub/menu.list, or /boot/grub/grub.conf, or whatever Fedora does with it.
4. Copy the appropriate Fedora entry that you want to use, into the ubuntu    /boot/grub/menu.lst file. Making sure that you use the proper syntax for the location of the root partition of the Fedora install. On say ."hdb", first partition, it would be (hd1,0).

If the syntax confuses you this is from the grub manual:

> 2 Naming convention

The device syntax used in GRUB is a wee bit different from what you may have seen before in your operating system(s), and you need to know it so that you can specify a drive/partition.

Look at the following examples and explanations:

     (fd0)

First of all, GRUB requires that the device name be enclosed with `(' and `)'. The `fd' part means that it is a floppy disk. The number `0' is the drive number, which is counted from zero. This expression means that GRUB will use the whole floppy disk.

     (hd0,1)

Here, `hd' means it is a hard disk drive. The first integer `0' indicates the drive number, that is, the first hard disk, while the second integer, `1', indicates the partition number (or the pc slice number in the BSD terminology). Once again, please note that the partition numbers are counted from zero, not from one. This expression means the second partition of the first hard disk drive. In this case, GRUB uses one partition of the disk, instead of the whole disk.

     (hd0,4)

This specifies the first extended partition of the first hard disk drive. Note that the partition numbers for extended partitions are counted from `4', regardless of the actual number of primary partitions on your hard disk.

     (hd1,a)

This means the BSD `a' partition of the second hard disk. If you need to specify which pc slice number should be used, use something like this: `(hd1,0,a)'. If the pc slice number is omitted, GRUB searches for the first pc slice which has a BSD `a' partition.

Of course, to actually access the disks or partitions with GRUB, you need to use the device specification in a command, like `root (fd0)' or `unhide (hd0,2)'. To help you find out which number specifies a partition you want, the GRUB command-line (see Command-line interface) options have argument completion. This means that, for example, you only need to type

     root (

followed by a <TAB>, and GRUB will display the list of drives, partitions, or file names. So it should be quite easy to determine the name of your target partition, even with minimal knowledge of the syntax.

Note that GRUB does not distinguish IDE from SCSI - it simply counts the drive numbers from zero, regardless of their type. Normally, any IDE drive number is less than any SCSI drive number, although that is not true if you change the boot sequence by swapping IDE and SCSI drives in your BIOS.

Now the question is, how to specify a file? Again, consider an example:

     (hd0,0)/vmlinuz

This specifies the file named `vmlinuz', found on the first partition of the first hard disk drive. Note that the argument completion works with file names, too.

That was easy, admit it. Now read the next chapter, to find out how to actually install GRUB on your drive. 

This is how i would try it, i have never done what you are doing but i would think that this would work just fine.

Good Luck

---

### Post by arjaybe on 2005-11-03
I have several distros on a second drive.  Here's the grub stanza for one of them:

title  Kubuntu 5.04, kernel 2.6.10
root	(hd1,1)
kernel	/boot/vmlinuz-2.6.10-5-386 root=/dev/hdc2
initrd	/boot/initrd.img-2.6.10-5-386

It sounds like your second drive has only one partition, so the (hd1,1) is probably (hd1,0) for you and the /dev/hdc2 is probably /dev/hdb1.  You'll have to substitute the vmlinuz and initrd.img with your Fedora ones.

Or, since there's a bootloader on the Fedora drive, you could try this:

title  PCLinuxOS p91, kernel 2.6.11
root  (hd1,2)
makeactive
chainloader +1

With the appropriate changes, of course.

---

