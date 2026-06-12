---
title: "Issue with automatically booting in to ubuntu"
date: 2008-12-07
forum: General Help
---

### Post by 90civichb on 2008-12-07
When I turn on the machine, grub auto loads the first entry in menu.lst which is Ubuntu 8.10. The splash screen with bouncing progress indicator then shows...

Shortly after I am dropped in to busybox with the following on the screen:

Starting Up ...
Loading, Please wait...

Gave up waiting for root device. Common Problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelat = (did the system wait long enough?)
   - check root = (did the system wait for the right device?)
  -Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda2 does not exist. Dropping to a shell!

BusyBox V1.10.2 (Ubuntu 1:1.10.2-lubuntu6) built-in shell (ash)
Enter 'help' for a list of built in commands

(initramfs)

After a short period of time, I can type in 'exit' and it will bring me to the standard ubuntu login screen. From that point on I have no issues.

I tried to follow what the screen was saying, but I can't seem to modify cmdline to include a rootdelay= line to the program. When I try to save it gives an input/output error. I tried several things including attempting to copy the file, modify it, and replace it, but that didn't work either. 

Any help would be awesome, as I am sure that adding a rootdelay=xx line to the cmdline would solve the issue. I can only assume that it takes a short while for the HD to be recognized, which is why I am able to exit to load the login screen.

I hope this is clear and a simple solution can be provided.

Note: /dev/sda2 is the correct device, and is an ext3 partition for this installation. It just doesn't show up for a few seconds after booting the machine. I have even checked /dev immediately after being thrown in to busybox and sda2 and the rest are not present at first. They will then show up shortly afterward, at which time I can type 'exit' and boot as it should.

---

### Post by 90civichb on 2008-12-08
I don't know the rules on bumping....

I don't think this is a hard problem to solve, I really would like to know how to edit /proc/cmdline. A google search has come up empty for me so far.

---

### Post by caljohnsmith on 2008-12-08
OK, how about trying this: when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the "kernel" line, press "e" to edit it, and add the following to the very end:
```
rootdelay=120
```
Press enter to save the change, then press "b" to boot. See if that works to boot Ubuntu, and if not, let me know exactly what happens. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent if it works. But first let me know if it works and we can go from there. :)

---

### Post by plucky on 2008-12-08
> I tried to follow what the screen was saying, but I can't seem to modify cmdline to include a rootdelay= line to the program. When I try to save it gives an input/output error. I tried several things including attempting to copy the file, modify it, and replace it, but that didn't work either.


Open a terminal and input ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.original
gksudo gedit /boot/grub/menu.lst
```

The first command will ask you to enter your password,but will not echo it, and will make a copy of your menu.lst file.

The second command will allow you to edit the menu.lst file where you can enter the "rootdelay=xx" option into the kernel line.

See if that works.

If not, copy and paste the output from a terminal window of these commands ```
sudo fdisk -l
sudo blkid
cat /boot/grub/menu.lst
```

Use [noparse]```

```[/noparse] blocks to enclose your output.(Makes it easier to read).


Good Luck

---

### Post by 90civichb on 2008-12-08
Adding rootdelay=120 worked. It took an extremely long time to boot, but it worked.

Can I try lowering this number and see what works best, or does it boot as soon as it can regardless of the time specified?

Thanks to both of you for the solution!

---

### Post by caljohnsmith on 2008-12-08
You definitely could try lowering that number until you find approximately what the threshold is when you start having the booting problem again. Once you find the threshold, I would recommend using a value at least slightly larger than the number you find just to ensure you don't have problems. Also, if you still have problems with an extremely long boot time, you could remove the "quiet splash" option at the end of the kernel line so you can watch all the boot messages on start up. That should help you find where the boot process is stalling. let me know how it goes. :)

---

