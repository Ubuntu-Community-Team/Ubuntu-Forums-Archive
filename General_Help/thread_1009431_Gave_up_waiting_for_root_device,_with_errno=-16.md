---
title: "Gave up waiting for root device, with errno=-16"
date: 2008-12-12
forum: General Help
---

### Post by mebegreedy on 2008-12-12
It wont let me directly boot into Ubuntu if the computer is off, the only way to get into Ubuntu is to load windows first and then restart from there. 

Any help would be greatly appreciated

Thanks,

---

### Post by unclejac on 2008-12-12
what is the spec of your machine? Running 8:10 i take it?

I'm guessing this is one of two things maybe: 

a bug associated with a certain motherboard (Intel D945Gnt)

See here: [Bug #290153: Fails to find boot device in Intel D945Gnt]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153")

There is a suggestion to insert a delay command to your menu.lst 

[I]"Proposed release note:

Boot failures on systems with Intel D945 motherboards have been reported. If this failure occurs, the system will drop to a busybox initramfs shell with a "Gave up waiting for root device." error. Wait a minute or two and then exit the initramfs shell by typing 'exit'. Booting should proceed normally. If it doesn't wait a bit longer and try again. Once the system boots, edit /boot/grub/menu.lst and add rootdelay=90 to the kernel stanza for your current kernel.[/I]"

so from gui use

```
sudo gedit /boot/grub/menu.lst
```

or from cli use

```
sudo nano /boot/grub/menu.lst
```


Or the uuid in the menu.lst doesn't match the uuid in the FSTAB ( i doubt this as it boots after going into windows . . .) 

Ok hope this helps . . .

---

### Post by clay_in_nj on 2008-12-12
I was having similar problems with a new install, and found out that the problem was my own, dumb, fault. (Who'd have guessed?) Turns out that I had my single WD drive jumpered for Master. Wrong! A single WD should usually have no jumper, or one on CSEL. Funny thing is, it worked fine that way with Windoze XP.

---

### Post by mebegreedy on 2008-12-12
Ya, the exit thing I saw that and that did not help at all, its an XFX 680i mobo. and my 2 drives I have are both sata with no jumpers on them.

XFX 680i
2x XFX 8800 GS
2 gigs Ocz ram
intel 2.4 quad core

---

### Post by caljohnsmith on 2008-12-12
Some people in the forums who have gotten that same error have found a workaround of using "rootdelay=120" or similar delay to the boot kernel line. To try it, reboot, select the Ubuntu entry from the Grub menu, press "e" to edit it, select the "kernel" line, press "e" to edit it, and add the "rootdelay=120" at the end of the line similar to:
```
kernel   /boot/vmlinuz-2.6.27-9-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash [COLOR="Blue"]rootdelay=120
[/COLOR]
```
Press enter to save the change, and finally "b" to boot. How about trying that and let me know if it helps at all.

---

### Post by mebegreedy on 2008-12-12
Yeah, no dice, still came up with the same error just took a whole lot longer to get there.

---

### Post by mebegreedy on 2009-01-05
been away from the comp for awhile, any more ideas?

---

### Post by KermitJr on 2009-01-19
Hello all.  I had to combine two suggestions from various posts.  First, I did remove the jumper since it was a WD and the only drive on the cable.

On the kernel boot line, I added:

irqpoll rootdelay=90

Still gives a few error messages, but it works!

Cheers!
Kermitjr

---

