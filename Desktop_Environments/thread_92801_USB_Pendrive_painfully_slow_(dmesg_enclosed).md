---
title: "USB Pendrive painfully slow (dmesg enclosed)"
date: 2005-11-20
forum: Desktop Environments
---

### Post by megamania on 2005-11-20
My pendrive is  s-l-o-w  under Hoary/Breezy. I started copying a 78Mb file and the estimated time was 3 hours! It looks like the computer sends data to the pendrive every 10 seconds or so (the light quickly blinks and then it stays off for a long while).

My motherboard manual says all the usb ports are 2.0.

This is the output of dmesg. It's the first time that I see it, so I'm not sure how to read it:

========================================================
[4296256.825000] usb 5-8: new high speed USB device using ehci_hcd and address 13
[4296256.916000] hub 5-8:1.0: USB hub found
[4296256.916000] hub 5-8:1.0: 1 port detected
[4296257.145000] usb 5-8.1: new high speed USB device using ehci_hcd and address 14
[4296257.196000] scsi11 : SCSI emulation for USB Mass Storage devices
[4296257.197000] usb-storage: device found at 14
[4296257.197000] usb-storage: waiting for device to settle before scanning
[4296260.074000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296260.074000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296260.255000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296260.255000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296262.198000]   Vendor: USB 2.0   Model: Flash Disk        Rev: 1.00
[4296262.198000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4296262.201000] SCSI device sdb: 1015808 512-byte hdwr sectors (520 MB)
[4296262.203000] sdb: Write Protect is off
[4296262.203000] sdb: Mode Sense: 00 26 00 00
[4296262.203000] sdb: assuming drive cache: write through
[4296262.207000] SCSI device sdb: 1015808 512-byte hdwr sectors (520 MB)
[4296262.210000] sdb: Write Protect is off
[4296262.210000] sdb: Mode Sense: 00 26 00 00
[4296262.210000] sdb: assuming drive cache: write through
[4296262.210000]  /dev/scsi/host11/bus0/target0/lun0: p1
[4296262.211000] Attached scsi removable disk sdb at scsi11, channel 0, id 0, lun 0
[4296262.213000] usb-storage: device scan complete
========================================================

Do you have any suggestions/ideas?

---

### Post by ram32 on 2005-11-20
i have the same problem with my msi mega player 521 usb 2.0 :(
but strange... it reads on normal speed ~2 mb/sec, but writes on 20-100 kb/sec

kernel 2.6.14.2 custom

---

### Post by megamania on 2005-11-21
any ideas? in my opinion, this is a major issue since it looks like it affects quite a few users.

is there a way I can check:
- if my usb ports are actually 2.0 (the manual of my motherboard says so, but I want to be sure)
- if they are properly recognized and configured as 2.0 by Ubuntu

But even if using Usb 1.0 ports, why is writing _so_ slow? I can't afford to wait 20 hours to write 500Mb to my pendrive. It takes less time to re-install windows and copy from that...   :-(

---

### Post by earobinson on 2005-11-21
Could this be a dma issue? (I know it can mess with cdroms and dvds not sure about usb)

Also you maye have more luck in the hardware section (to me this feals more like a hardware problem than anything else), you should be able to move this thread over.

PS
> Location: /Italy/Bologna/home
lol, I just may steal that idea lol

---

### Post by megamania on 2005-11-21
[QUOTE=earobinson]Could this be a dma issue? (I know it can mess with cdroms and dvds not sure about usb)

Also you maye have more luck in the hardware section (to me this feals more like a hardware problem than anything else), you should be able to move this thread over.[/QUOTE]

You may be right, but I have no idea how to move a thread - I didn't find a way to do so.

[QUOTE=earobinson]
PS
Location: /Italy/Bologna/home 
lol, I just may steal that idea lol[/QUOTE]

sorry, it's not under GPL  :-) - but if you solve my problem, I'll give you the rights to use it.  :D

---

### Post by earobinson on 2005-11-21
lol
you should be able to click thread tools to move the thread.

I did some searching and I have found this [http://www.ubuntuforums.org/showthread.php?t=79688&highlight=usb+pendrive](http://www.ubuntuforums.org/showthread.php?t=79688&highlight=usb+pendrive) apparently it is a bug. But Ill keep looking and if I find anything ill let you know. Also if you fix this let us know.

Also you may want to look at this [http://www.ubuntuforums.org/showthread.php?t=58603&highlight=usb+pendrive](http://www.ubuntuforums.org/showthread.php?t=58603&highlight=usb+pendrive)

---

### Post by megamania on 2005-11-21
[QUOTE=earobinson]lol
you should be able to click thread tools to move the thread.
[/QUOTE]

sorry, I don't have that option in thread tools.

[QUOTE=earobinson]
apparently it is a bug. But Ill keep looking and if I find anything ill let you know. Also if you fix this let us know.

Also you may want to look at this [http://www.ubuntuforums.org/showthread.php?t=58603&highlight=usb+pendrive](http://www.ubuntuforums.org/showthread.php?t=58603&highlight=usb+pendrive)[/QUOTE]

I had checked both threads before (I try to search before asking), but still have to try changing the order modules are loaded.
It would just be enough to know if it's a bug (I think it is) or not. If it's the first, I'll just sit down and wait without going crazy looking for a solution.

---

### Post by earobinson on 2005-11-21
*extra points for searching first*

Im betting on a bug for now. Weird you dont have that option. If you are really keen on moving this post send a msg to aysiu.

---

### Post by megamania on 2005-12-12
I'm using this old thread that I started a few weeks ago because my pendrive has suddenly started to work faster!

Yesterday a friend of my came with his pendrive and it worked like a charm. I thought it was a matter of different brands, but when I tried mine it was WAY faster than it used to be.

I hadn't used my pendrive for a couple of weeks, so I'm wondering if in the meantime the slow writing speed was acknowledged to be a bug and fixed with one of the updates... does anybody know anything about it?

And is there a way to test the actual throughput of my pendrive?

---

### Post by ranf on 2005-12-12
[QUOTE=megamania]
And is there a way to test the actual throughput of my pendrive?[/QUOTE]
Take a 100MB file and copy it over with time:

time cp 100mb_file /media/usbdisk

---

### Post by earobinson on 2005-12-12
So I guess that it was a but then. good to see you got it working :)

*Thanks for the update also*

---

### Post by megamania on 2005-12-12
[QUOTE=ranf]Take a 100MB file and copy it over with time:

time cp 100mb_file /media/usbdisk[/QUOTE]

Great tip, thanks. I'll try (but I don't know what value to expect in order to benchmark it...).

_Earobinson_:
After all I've been learning in this forum, the least I can do is try giving something back!

---

### Post by earobinson on 2005-12-12
you could always post your time, then hope some one else will do the same (no pen drive :()

---

### Post by megamania on 2005-12-13
[QUOTE=earobinson]you could always post your time, then hope some one else will do the same (no pen drive :()[/QUOTE]

I still have to time it, but would the timing be reliable? Wouldn't the data caching considerably affect the result?

---

### Post by earobinson on 2005-12-13
probaly, It was the best idea I could come up with. Enoughf people doing this should give us and idea, at least a ballpark.

---

### Post by megamania on 2005-12-13
Right. And now that I think of it, the cache would probably affect smaller transfers. 100Mb should be pretty (i.e. more or less :) ) reliable.

I'll check it tonight and get back with the results.

---

### Post by ranf on 2005-12-13
[QUOTE=megamania]Right. And now that I think of it, the cache would probably affect smaller transfers. 100Mb should be pretty (i.e. more or less :) ) reliable.

I'll check it tonight and get back with the results.[/QUOTE]
I only have a 128MB drive. So I suggested 100MB. But you can also use a larger one, if it fits.

I created the file this way:
```
dd if=/dev/zero of=100mb count=100 ibs=1024k
```

After some experimenting with this, I realize that a simple "time cp ..." doesn't give real numbers. cp returns quite fast but the buffers are not yet flushed to the pendrive.
Here is a better one:
```
echo "cp 100mb /media/usbdisk/" >speed.sh
echo sync >>speed.sh
time sh speed.sh

```
For 100MB and my USB 1.1 drive I get:
```
real    1m55.234s
user    0m0.023s
sys     0m1.077s

```

That means 100MB/115 sec =0.9 MB/sec

---

### Post by earobinson on 2005-12-13
thanks for the info
*extra points for the great documentation*

---

### Post by megamania on 2005-12-13
[QUOTE=ranf]I only have a 128MB drive. So I suggested 100MB. But you can also use a larger one, if it fits.

For 100MB and my USB 1.1 drive I get:
```
real    1m55.234s
user    0m0.023s
sys     0m1.077s

```

That means 100MB/115 sec =0.9 MB/sec[/QUOTE]

Excellent solution, thanks!

I have a bigger pendrive (512mb), but thought I should stick to the 100Mb size in order to make comparisons easier. This is what I got:

```

real    0m35.694s
user    0m0.013s
sys     0m0.808s

```

= 2,86 Mb/sec

Now I can say that my pendrive is NOT painfully slow anymore! :-)  By the way, does anybody know what the optimal throughput should be with an USB 2.0 device?

Once again, thank you for the great benchmarking tool. I knew that the cache would cause unreliable results, but had no idea how to solve it...

---

### Post by schneiko on 2006-01-05
I just had the same problem with a *very* slow (100kb/s or less) USB 2.0 external hard-drive. I tried a lot of things, but nothing helped. Sometimes, I could copy a few files very fast, then it would take hours.

Well, to make it short: I solved the problem by stopping "athcool" (powersaving tool). I just tried this because it was one of the things I didn't try before ;) And it worked.

As soon as I enable athcool and do "hdparm -t /dev/sda/", the external drive is extremely slow. Disabling athcool gives me about 20mb/s, which is ok, I think. The speed.sh-script tells me the same as hdparm does:

```
$ time sh speed.sh

real    0m5.891s
user    0m0.011s
sys     0m1.053s

```

---

