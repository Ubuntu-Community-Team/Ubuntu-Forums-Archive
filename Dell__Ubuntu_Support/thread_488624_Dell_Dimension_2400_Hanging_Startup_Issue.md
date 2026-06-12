---
title: "Dell Dimension 2400 Hanging Startup Issue"
date: 2007-06-30
forum: Dell  Ubuntu Support
---

### Post by notaloafer on 2007-06-30
**Computer:** Dell Dimension 2400
**OS:** Ubuntu Feisty (Just downloaded the other day, up-to-date)
**System Components:** Pentium 4 @ 2.8GhZ, 1GB RAM, 80GB HDD

**Problem:** I resolved the issue with the no graphic display at startup but now at the Ubuntu splash screen progress (the thing that loads right after GRUB finishes) it goes about 1/2 a cm with progress and just hangs there for like 2-3 minutes and THEN loads up. Once the OS has loaded though everything is running fast as usual.

How do I fix the hanging splash screen? It's taking way too long to boot this thing!

Thanks!
-Eric.

---

### Post by neptho on 2007-06-30
At the grub boot message, press 'esc', then choose 'recovery'.  You should be able to see where it's hanging up there.  My guess is it's the floppy drive, but we need to know more before we can help.

---

### Post by notaloafer on 2007-06-30
[14.96 ] USBCore: registered new interface driver usbhid
[14.96 ] drivers/usb/input/hid-core.c: v2.6 USB HID Core Driver 
[ 43.81] ata2.00: qc timeout (cmd 0xef)
[43.81 ] ata2: failed to recover some devices, retrying in 5 secs
[ ]ata2.00: qc time out (cmd 0x3f)
[79] ata2.00: limited speed to UDMA / 33: PI03
Then it says something about disabling ata. after this it speeds up and starts loading stuff and then I'm in command line linux

ACPI Interrupt 000....... : GSI -18 (level, low) IRQ 18
Hangs there for about 15 seconds as well.


**By the way I use a Belkin KVM... that shouldn't cause any problems right?**

Sorry about not posting the whole sequence but I don't know how to do that :P

PS- I just removed my FDD and my CDROM drives from the boot sequence but it didn't make any difference.

---

### Post by neptho on 2007-06-30
I've seen strange hangs with KVMs before, but this may be an ACPI problem.  This time, in grub, press 'esc', and highlight the first.  Press 'e' for edit, then edit the kernel config line (that's the one that says: kernel ... root=...),  and remove the splash data, then add a space, then "noacpi"

It'll look something like this:

```
kernel=/boot/vmlinuz-2.6.20-16-generic root=UUID=b6a26ea2-03a5-4936-8fa0-6e0c2e5be158 ro noacpi
```

Press 'b' to boot, and see if it hangs.  If it doesn't, make sure everything else works, because disabling ACPI will disable various dual core CPU functions for many machines.  If everything seems to 'work ok', edit /boot/grub/menu.list and add 'noacpi' to the 'kopt' line.

Good luck!

---

### Post by notaloafer on 2007-06-30
Still the entire boot is haulted on the line
[41] drivers/usb/input/hid-core.d: v2.6 USB HID core driver
[69] ata2.00: qc timeout (cmd 0x3f)
[69] Failed to recover some devices, retrying in 5 secs

It seems its trying to fix itself it goes through.
1: Failed to boot some devices
2: failed to set xfermode
3: limited speed to UDMA/33:PI03

Eventually though it does boot

Any ideas?

-Eric.

By the way my line included : ro **quiet** splash

instead of without the quiet... does that make a difference?

PSS- When i took out the quiet it just showed me two errors
[50] ata2.00: failed to set xfermode (err_mask=0x4)
same for [80 seconds] and [110 seconds]

After that the list of lines goes so fast I cant see whats going on :P

---

### Post by neptho on 2007-06-30
> **notaloafer said:**
> Eventually though it does boot

Any ideas?

-Eric.

Ok, good, that's not it.  That's usually a bear.  What's plugged into your USB ports?

Try removing USB 2.0 support and keep USB 1 support enabled as so:

```
%sudo sh -c 'echo blacklist ehci_hcd > /etc/modprobe.d/blacklist-ehci'
%sudo update-initramfs -u -k `uname -r`
```

Then try another reboot without the splash screen to see if it hangs at the same place.  If it doesn't, it's one of those problematic USB 2 support issues.  If that doesn't help, you can re-enable USB 2.0 as such:

```
%sudo rm /etc/modprobe.d/blacklist-ehci
%sudo update-initramfs -u -k `uname -r`
```

Oh, and the quiet thing just tells it to not print all of that ugly kernel info to the screen.  It's best to not have it there when debugging, but it's entirely superficial.

I assume you're using a 2.6 kernel?   The ATA error is usually due to libata's SATA support.  Does your CDROM show up as 'scdX' or 'cdX'?

---

### Post by notaloafer on 2007-06-30
> **neptho said:**
> Ok, good, that's not it.  That's usually a bear.  What's plugged into your USB ports?

The only thing plugged in is my USB from my KVM. I think I might know why its doing this

I have a KVM with two USB ports (keyboard / mouse) and a standard port for a monitor.
I am currently using a wireless keyboard/mouse plugged into **1** data point thats plugged into just the keyboard USB on my KVM.

The KVM takes the keyboard/mouse USB and composes them into 2 outgoing USB's. 

Here is the KVM I have: 
[http://images.belkin.com/F1DG102U/STD1_F1DG102U.jpg](http://images.belkin.com/F1DG102U/STD1_F1DG102U.jpg)

I'm only using the Keyboard USB slot on the KVM since the keyboard/mouse are gathered on one data point.

Thanks
-Eric.

---

### Post by notaloafer on 2007-06-30
Actually we can rule out the KVM, I just unplugged my computer moved it into my dads and hooked up his standard mouse and standard keyboard to it with a standard monitor and I still get the exact same issues.

How do I go about disabling USB 2.0 ? I didn't quite understand where to enter those commands out (I'm a ubuntu/linux newbie)..

Thanks so much
-Eric.

---

### Post by neptho on 2007-06-30
> **notaloafer said:**
> Actually we can rule out the KVM, I just unplugged my computer moved it into my dads and hooked up his standard mouse and standard keyboard to it with a standard monitor and I still get the exact same issues.

How do I go about disabling USB 2.0 ? I didn't quite understand where to enter those commands out (I'm a ubuntu/linux newbie)..

Thanks so much
-Eric.

The commands above disable USB 2.0 support from loading when you boot, and since Ubuntu loads a RAM disk to boot (for various reasons), this tells it to update your settings after you disable the USB 2.0 support.  It will still work as USB 1.1.  If that resolves your problem, great - if not, I'm stumped, because the 2400 series has had so many different options in the last few years I've dealt with them.  :)

---

### Post by notaloafer on 2007-07-01
Tried it, no luck :( any more ideas? I really like Ubuntu and am setting it up for server use but I would really like to get this fixed before I deploy!

Thanks!
-Eric.

---

### Post by bluknight on 2007-07-01
> **notaloafer said:**
> 
[69] ata2.00: qc timeout (cmd 0x3f)
[69] Failed to recover some devices, retrying in 5 secs
<snip>
PSS- When i took out the quiet it just showed me two errors
[50] ata2.00: failed to set xfermode (err_mask=0x4)
same for [80 seconds] and [110 seconds]

Do you have SATA drive mixed with ata or pata drives in your system? Then as on post #6 you shd modprobe piix or better still try what's suggested here:
[http://ubuntuforums.org/showthread.php?t=421588&highlight=piix](http://ubuntuforums.org/showthread.php?t=421588&highlight=piix)

Won't hurt to do that - as I booted my Feisty by using Edgy kernel and initramfs that way.

HTH

---

### Post by notaloafer on 2007-07-01
I don't have anything but 1 80GB IDE 7200RPM HDD.

Thanks
-Eric

---

### Post by neptho on 2007-07-02
Hi Eric,

I'm stumped, without having a 2400 around to play with.. even a semi-similar model.  Go ahead and back out my USB 2.0 driver removal if you want (this was the second set of instructions), it won't hurt you, though, to keep it as it is, things that are USB 2.0 will just operate at USB 1 speeds (keyboard and mouse are USB 1 anyhow).

---

### Post by larusa on 2007-10-09
Hi there!

Maybe it's late, but I just had this problem today (still haven't tried any solution posted) and after googling a little bit, these two threads may resume everything. 
Adding irqpoll to the kernel line in /boot/grub/menu.lst or set CD-ROM to use cable selec. I suppose this depends on what ata device causes the problem....

[http://ubuntuforums.org/showthread.php?t=414002&page=4](http://ubuntuforums.org/showthread.php?t=414002&page=4)

[INDENT]"Been having this problem myself. Set your CD ROMs to use Cable Select, not master/slave. When I did this, the boot lag ceased."[/INDENT]

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826)

[INDENT]"Add the word 'irqpoll' (without quotes) to the kernel line in /boot/grub/menu.lst thus:

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash irqpoll

Then Feisty will boot faster, and the Liteon CD burner will be recognised."[/INDENT]

PS; Unfortunately, as I read in another thread, it seems that update-grub will rewrite /boot/grub/menu.lst and erase the irqpoll. Anyway I just saw this problem in this thread, and suppose this only happens when the grub menu is rewriten, which i tend to think happens just when a new kernel image is installed.
[http://ubuntuforums.org/showthread.php?t=440122](http://ubuntuforums.org/showthread.php?t=440122)

Hope anyway you have it solved. I'm going to try now with irqpoll since I don't feel like opening the pc now..- ;-)

---

