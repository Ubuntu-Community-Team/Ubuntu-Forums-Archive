---
title: "GRUB problems.  Won't autoboot."
date: 2008-12-07
forum: General Help
---

### Post by bluefox815 on 2008-12-07
Hello.  I am new to this community, so I apologize if this post is in the wrong section.

So, my problem is that I have Ubuntu 8.10 32-bit installed on two computers, each using the same disc.  The first computer installed perfectly, no problems whatsoever.  The other computer, however, is not auto-booting to Ubuntu from GRUB.  Instead, GRUB goes directly into Command-line mode, there is no countdown or anything.  I can still boot to Ubuntu by typing the following commands:

root (hd0,0)
kernel /vmlinuz root=/dev/sda1 vga=ext
initrd /initrd.img
boot

I'm unable to post the menu.lst file, but I've added my own configuration, which still failed to work:

title Custom Ubuntu
(commands entered above)
quiet

I have tried this with/without root, quiet, and boot commands.  I've also tried savedefault in the menu.lst file.

And lastly,  the "default" variable is set to 0, and "timeout" (or is it countdown?) is set to 5.  Either way, the countdown timer is set to 5 seconds.

Any help you can give me is appreciated.

---

### Post by falcon61102 on 2008-12-07
If you can boot up with a LiveCD and edit the GRUB to reflect the changes that you manually entered, you should be good.  Open up the menu.lst that's on your HD and make sure that they reflect what you have above.

EDIT: And welcome to the forums.

---

### Post by bluefox815 on 2008-12-07
Well, I can't really boot to a LiveCD on the computer, I had to remove the HDD and place it into this one I'm on now.  That turns out to be quite a hassle, so how do I go about doing this all on ubuntu?

Also, I was able to get the menu.lst file on a flash drive, so I have attached it to this post as a text file.  The kernel and initrd images it refrences to DO exist as spelled.

---

### Post by caljohnsmith on 2008-12-07
How about when you boot the drive and get the Grub command line, try the following:
```
grub> cat (hd0,0)/boot/grub/menu.lst
```
And does that show the menu.lst? If not, also try typing the following without hitting enter:
```
grub> null (hd0,0)/boot/grub/
```
The press TAB for tab-completion, and does that show the menu.lst as one of the listed files? If not, what files does it list?

---

### Post by falcon61102 on 2008-12-07
Does the UUID for the partition match the one that is in the GRUB?  
You can check UUID's by running:
```
blkid
```

---

### Post by bluefox815 on 2008-12-07
cat displayed the menu.lst file.

null with TAB listed "menu.lst" and "menu.lst~" as possible completions (among others).

---

### Post by caljohnsmith on 2008-12-07
So can you boot a Live CD to access the drive? Or how are you accessing the drive right now (how did you get the menu.lst)? If you can use your Live CD, how about opening a terminal (Applications > Accessories > Terminal) and reinstall Grub to the MBR (Master Boot Record) of the drive by doing:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And please post the output of all the above commands. Next please post:
```
sudo fdisk -lu
```
Then reboot, and let me know if you still get dumped into the Grub command line. Also, you mentioned the HDD is in another computer now? So you are getting dumped into the Grub command line when you boot that HDD on either computer?

---

### Post by bluefox815 on 2008-12-07
My BIOS will not boot to a CD, but I can boot to Ubuntu.
I'm capable of booting Ubuntu, but not without entering a few commands, the process of which I am tired of repeating.

The UUID's are the same.

sudo fdisk -lu  says that my "Linux" partition is /dev/sda1

I have already checked that partitions match and files pointed to exist.


And lastly, may I reinstall grub with Ubuntu, or is the LiveCD required?  If I can't, will "sudo grub" just fail to execute?

EDIT:  "sudo grub" took me to the familiar GRUB prompt, I have run the root command but have not run the setup command, as I'm waiting for an "OK" so that I don't destroy this computer.

I have not tried the HDD on any other computer, it has stayed in that computer with no runs on other computers.

---

### Post by caljohnsmith on 2008-12-07
You can reinstall Grub from your Ubuntu install, that is OK. It would help if you could post the full output of the fdisk command though so I can get an idea if you might have a problem with your HDD's partition table; sometimes a slightly corrupt partition table can cause Grub to behave really strange. Also, please post the full output of the Grub commands so I can check that the installation went as it should.

---

### Post by bluefox815 on 2008-12-07
I reinstalled GRUB and it seems to be autobooting now.  Thank you for your help, everything is working now.  Although I do have a side question:  How much RAM is recommended for use with a 400 MHz processor?  I currently have 512 MB, but I don't know if that's what would be considered "bottlenecking" the CPU.

---

### Post by falcon61102 on 2008-12-07
Glad you got it working.

The RAM ammount should really depend on usage.  If you notice your system dumping a lot of it's processes to the SWAP then you may be able to benefit from some more RAM but if not, then you should be good.

---

### Post by caljohnsmith on 2008-12-07
> **bluefox815 said:**
> I reinstalled GRUB and it seems to be autobooting now.  Thank you for your help, everything is working now.  Although I do have a side question:  How much RAM is recommended for use with a 400 MHz processor?  I currently have 512 MB, but I don't know if that's what would be considered "bottlenecking" the CPU.
That's great news, I'm glad that did the trick. About how much RAM to have, it really depends mostly on whether you get close to maxing it out and then having to use alot of your swap space as virtual RAM like falcon61102 mentioned; you can check by doing the command:
```
free
```
Anyway, cheers and have fun with Ubuntu. :)

---

