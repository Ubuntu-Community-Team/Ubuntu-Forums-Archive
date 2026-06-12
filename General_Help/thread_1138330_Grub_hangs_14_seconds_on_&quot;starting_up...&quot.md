---
title: "Grub hangs 14 seconds on &quot;starting up...&quot;"
date: 2009-04-26
forum: General Help
---

### Post by rocketman768 on 2009-04-26
So, whenever I choose Ubuntu from the grub menu, it hangs for 14 seconds on a black screen with "Starting up..." before actually starting up. Since Jaunty is supposed to be so fast, I would not like to waste this time on a Grub issue.

---menu.lst
```

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a8415bc8-5df2-477e-98d0-dfe85d81d80b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

# This entry automatically added by the Debian installer for a non-linux OS on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1

```

I'm pretty sure I had to switch the order of my drives in BIOS if that might be an issue.

---

### Post by rocketman768 on 2009-04-26
Ok, I switched my drives in BIOS, and still the same lag. I only briefly see the message when starting XP.

---

### Post by Tom_T on 2009-04-26
I've just installed Jaunty onto an Acer Aspire One D150 and i also get the delay on 'Starting Up" !!

It's only 5 - 10 seconds but why the wait ??

Hope this can be resolved for both of use :)

---

### Post by Tom_T on 2009-04-26
Just read another forum post that suggest it's an issue with menu.list

I'll have a play with this tomorrow and see what happens..

---

### Post by Tom_T on 2009-04-27
I've started a nw thread re my specific problem.. If I get any answers I'll post back here.

---

### Post by danwood76 on 2009-04-27
This delay is when its decompressing the intramfs, if you set the display mode from quiet to verbose you will see that it is actually doing stuff during that time.

---

### Post by blazemore on 2009-04-27
[http://ubuntuforums.org/showthread.php?t=1139546](http://ubuntuforums.org/showthread.php?t=1139546)

---

### Post by Tom_T on 2009-04-29
> **danwood76 said:**
> This delay is when its decompressing the intramfs, if you set the display mode from quiet to verbose you will see that it is actually doing stuff during that time.

Is there anyway to speed that up ??
On my main laptop it starts instantly.. 

On my wife Acer One 8.9" netbook there is a very slight delay 2 seconds.

On my Acer One 10.1" netbook the delay is a lot longer..

---

### Post by rocketman768 on 2009-06-16
Turns out that disabling Legacy USB in my BIOS fixed this problem for me.

---

### Post by TwiceOver on 2009-10-22
Seems like a dead thread, but I am having the same issue on an Acer 4810tz.

This happens under both 9.04 and 9.10 so it must be an issue with the laptop or grub itself.

I am currently using 9.10 and get a quick flash of "Grub Loading" which disappears to a blinking cursor for ~10 seconds.

Does anyone know how to change the verbose setting for Grub2 in 9.10?  I tried removing "quiet splash" from my boot options but that didn't help.  (yes I did update-grub).  I'd like to see what grub is doing during this time.

---

