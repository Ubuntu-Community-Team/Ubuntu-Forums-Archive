---
title: "won't wake from hibernate"
date: 2005-12-08
forum: General Help
---

### Post by DaveRowell on 2005-12-08
logged out from Gnome and checked "hibernate" - monitor went into sleep mode then after a minute or so the power light went off, longer than XP but otherwise similar behavior

now when I boot Ubuntu 5.10 all I get is "GRUB__" in the upper left corner of the screen - 3 finger salute reboots - XP is still alive

Compaq SR1265 - AMD Athlon XP 3200+ - VIA 53G Unichrome IGP on A7V8X-LA motherboard - 512 MB

QUESTIONS:
1 - how can I recover my Ubuntu installation?  I can get into a terminal with the install CD in rescue mode but I haven't the foggiest idea of what to do once I get there.  Please dumb down the response I am really a Ubuntu nubie.  [I also have an older live CD]
2 - what must I change to allow hibernation longterm?

---

### Post by malmjako on 2005-12-08
When does "GRUB__" appear? Do you get the Grub menu?

IF the Grub menu does appear, try adding "noresume" to the kernel boot options, by first selecting your Ubuntu kernel in the list (with up/down arrows), pressing "e" and adding the word noresume to the end of the options list. Press return, then boot with that configuration, by pressing "b". (Note: This is just off the top of my head, as I'm at work on a Windows machine at the moment. Below the Grub menus you can find the available commands. If my instructions are contradicting to those, then I just didn't remember correctly.) (Note 2: If the system boots, you probably won't be able to hibernate without first rebooting without the noresume option.)

Another way to get into your system might be to erase the data on your swap partition, which is where hibernate stores RAM, but It doesn't feel like the best solution to me for some reason...

I have no idea why you got this problem, so unfortunately I can't help you with finding the long term solution. This is just a way to get you back into your system, hopefully... Good luck!

---

### Post by DaveRowell on 2005-12-08
I get no menu - nothing onscreen except GRUB__

nothing except 3 finger salute seems to be recognized

---

### Post by malmjako on 2005-12-08
Then I would suggest you try reinstalling grub. Try the instructions on the following thread: [http://ubuntuforums.org/showthread.php?t=76652]("http://ubuntuforums.org/showthread.php?t=76652")

---

### Post by DaveRowell on 2005-12-10
OK, I've reinstalled GRUB in 2 different ways - as you suggested and, after that failed, by booting my SLAX on a stick (USB pen drive) changing root to the hard drive then using GRUB itself to make the change.

Same result - nothing changed

There must be a file somewhere that is written wrong that I could delete or something to get Ubuntu to boot again.  Ideas?

---

### Post by malmjako on 2005-12-12
I'm out of suggestions, sorry...

---

### Post by DaveRowell on 2005-12-12
Well thanks for your efforts anyway  ;-)

---

### Post by Adrian on 2005-12-19
[QUOTE=DaveRowell]logged out from Gnome and checked "hibernate" - monitor went into sleep mode then after a minute or so the power light went off, longer than XP but otherwise similar behavior
[/QUOTE]

I had this problem too. Instead of hibernating from the log out window, try doing it as root from the terminal. It worked for me.

```

sudo -s
echo -n "disk" > /sys/power/state

```

---

### Post by DaveRowell on 2005-12-19
Thanks for the responses - I appreciate them all.

I reinstalled Ubuntu with GRUB installed on / .  When I rebooted to finish the install I found myself in the same mess as before!  I had to make a new copy of the first sector on the Ubuntu boot partition for XP's loader to use - then I could boot Ubuntu again.  I probably didn't need the reinstall :( 

Now I wonder what and why the content of the first sector of the Ubuntu boot partition was changed while I was running.  It was changed tho as I had a backup copy of the original and that wouldn't work either!  :confused: 

So, given that, I expect that this will happen again some day.  At least when it does I'll have a clue.

---

### Post by simspace on 2007-03-26
I know this thread's old however I wanted to say thanks.

After a hibernate, my hda1 device was not found. I could only load a cmd prompt. 

After following the grub menu edit intructions above in post#2, I was back up and running. 

Thanks again!

---

### Post by Inquisitive Alex on 2007-12-22
I have a similar problem. I cannot cause system to resume after hibernate. The grub menu appears and I can only start my computer "from scratch" like after reboot. My /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=992c08c7-8845-4a4b-9d46-a070d25200f0 /     ext3    defaults,errors=remount-ro 0       0
# /dev/hda7
UUID=e413c8d3-f4c0-4ff9-8baa-db97beff48f8 /home     ext3    defaults        0       0
# /dev/hda6
UUID=63abf944-c0cd-43eb-877d-a5e6fdf7f5cc none            swap    sw              0       0
# /dev/hda1
UUID=1d4428a8-790f-4e8e-a1bd-e3d0cf4d34eb /boot     ext3    defaults        0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
 and here is my /boot/grub/menu.lst
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=992c08c7-8845-4a4b-9d46-a070d25200f0 resume2=swap:/dev/sda6 ro quiet splash hwprobe=-modules.pata
initrd          /initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=992c08c7-8845-4a4b-9d46-a070d25200f0 ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=992c08c7-8845-4a4b-9d46-a070d25200f0 ro quiet splash
initrd          /initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=992c08c7-8845-4a4b-9d46-a070d25200f0 ro single
initrd          /initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
quiet

```

---

