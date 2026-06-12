---
title: "Intrepid remaing over 60 seconds in &quot;Reading Files Needed to Boot&quot;"
date: 2009-01-01
forum: General Help
---

### Post by Belerophon on 2009-01-01
You've gotta help me here :(

My boot is very slow, it gets stuck in "Reading Files needed to boot", during which the hdd led stays on. I have attached the bootchart, and the log.

I see some error about compiz.real in the log, don't know if this has something to do with it.

I'm running ubuntu, upgraded from hardy to intrepid, on a Toshiba A100.

Please help.

Thanks.

---

### Post by Belerophon on 2009-01-03
*Bump*

---

### Post by Belerophon on 2009-01-08
Please...lol...I can't believe I'm the only one with this problem...

I don't understand much of these kernel messages, but from one point to another it passes 40 sec and the next message is about some compiz thing, which I find strange. Compiz at this stage of boot??
```
Jan  8 01:07:14 belerophon-laptop kernel: [25055.116092] hub 3-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Jan  8 01:07:14 belerophon-laptop kernel: [25055.116111] usb 3-1: USB disconnect, address 14
Jan  8 01:07:15 belerophon-laptop kernel: [25055.400068] usb 3-1: new low speed USB device using uhci_hcd and address 15
Jan  8 01:07:15 belerophon-laptop kernel: [25055.568608] usb 3-1: configuration #1 chosen from 1 choice
Jan  8 01:07:15 belerophon-laptop kernel: [25055.593734] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input20
Jan  8 01:07:15 belerophon-laptop kernel: [25055.637518] input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.2-1
[COLOR="Red"]Jan  8 01:47:49 belerophon-laptop kernel: [27490.063444] compiz.real[17949]: segfault at 50 ip 08055c8c sp bf901d00 error 4 in compiz.real[8048000+34000][/COLOR]
Jan  8 01:49:52 belerophon-laptop kernel: Inspecting /boot/System.map-2.6.27-9-generic
Jan  8 01:49:52 belerophon-laptop kernel: Cannot find map file.
```

Thanks.

---

### Post by Moushika on 2009-01-10
I've exactly the same problem on a HP Compaq 6715b laptop.

The "Reading files needed to boot" step takes between 1 and 2 minutes and the harddrive led is continuously on.
However, I haven't any error about compiz in my log.

Does anybody have an idea ?

---

### Post by Belerophon on 2009-01-10
Please read an try this:
[http://ggts.net/2008/05/13/reading-files-needed-to-boot/](http://ggts.net/2008/05/13/reading-files-needed-to-boot/)

This problem and fix appear in many forums.

I've already did that, however that was not my problem. All my UUID match. Maybe you have better luck than I.


Something like 2 minutes is way too much for a boot period. I'm damned. ](*,)

---

### Post by Moushika on 2009-01-10
My UUID match. I don't think the problem is about UUIDs.

I tried to boot with the acpi=off option, and it worked!!
But if I disable ACPI, then I have no shutdown, no suspend, no fan and cooling support, so the CPU overheats. ACPI is a very important part of PCs.

We must find another solution.

---

### Post by Moushika on 2009-01-11
I found the solution!!

Edit /boot/grub/menu.lst.
Find this line :
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=your_uuid ro quiet splash
and add these options :
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=your_uuid ro quiet splash highres=off nohz=off irqpoll

For me it worked. I hope it will work for you too.
Tell me if it doesn't work.

---

### Post by Belerophon on 2009-01-11
> **Moushika said:**
> I found the solution!!

Edit /boot/grub/menu.lst.
Find this line :
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=your_uuid ro quiet splash
and add these options :
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=your_uuid ro quiet splash highres=off nohz=off irqpoll

For me it worked. I hope it will work for you too.
Tell me if it doesn't work.


:(

It did not work for me. I tried one adding one kernel parameter at a time, booted one time with highres, another with just nohz...

Also, a time ago, I saw something about disabling "legacy usb support" in the bios...I tried these kernel parameters with this option on and off.

(By the way, I have "quiet verbose", instead of splash, but I did not bother to change it, as this has nothing to do with the problem...! Right??)

I like knowing a little about what I'm doing, and I did not knew about these kernel parameters, so I did some investigation:
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)

This shows, for kernel 2.6.26 (however I am with 2.6.27) the available kernel parameters. Just to know a little about what we're doing. May be of use to some of us...

Any more ideas?
I really don't know what's going on, but I'll try reading further about kernel parameters, to see if there's something I can tweak...there must be!

Anyway, thanks a lot for the idea Moushika.

---

### Post by Moushika on 2009-01-12
Try the nolapic_timer option.
It also works instead of nohz=off.

---

### Post by Belerophon on 2009-01-12
> **Moushika said:**
> Try the nolapic_timer option.
It also works instead of nohz=off.

Still no luck...

---

### Post by Moushika on 2009-01-14
Try:
noapic nolapic nolapic_timer

---

### Post by Moushika on 2009-01-14
Try this (all at the same time):
noapic nolapic nolapic_timer

edit: oops! double post

---

### Post by Belerophon on 2009-01-14
> **Moushika said:**
> Try this (all at the same time):
noapic nolapic nolapic_timer

edit: oops! double post

That went bad:

I had this line of boot:
```
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0428a40b-755e-4dcf-aaaf-f6cdb838b78c ro quiet verbose noapic nolapic nolapic_timer
```

It still hanged for an endless time in "reading files bla bla" and on login screen the system was completely unresponsive: no CTRL+BACKSPACE, CTRL+ALT+DEL, no no console, no nothing. Had to shutdown manually...

---

### Post by Moushika on 2009-01-15
> It still hanged for an endless time in "reading files bla bla" and on login screen the system was completely unresponsive: no CTRL+BACKSPACE, CTRL+ALT+DEL, no no console, no nothing. Had to shutdown manually...
Mmmhh... That's strange.
noapic and nolapic should solve this crash.

I keep on searching. I tell you if I have news.

---

