---
title: "Firewire"
date: 2006-06-19
forum: Desktop Environments
---

### Post by ColinG on 2006-06-19
Have installed Kino but when I try to capture video across firewire I get the dreaded "raw1394 kernel module not loaded." I would have thought this ws a thing of the past now!

Is there a workaround please?

Many thanks
Colin

---

### Post by dim_hyder on 2006-06-19
Hi Colin,

Sound as if you need to change the permissions on /dev/raw1394

do the following:

sudo chmod 777 /dev/raw1394

Hope this solves it.

Cheers,

Pete

---

### Post by ColinG on 2006-06-19
Hi Pete,

That's fixed it =D> Excellent!

Many thanks
Colin

---

### Post by endura29 on 2006-09-04
I've also tried the **sudo chmod 777 /dev/raw1394** and have run Kino as root, but am still getting the **"raw1394 kernel module not loaded"** error.

One thing that I've noticed to be different thus far is I might be having problems due to **ohci1394** which no one else seems to mention. 

When I do a **tail -f /var/log/messages** I get the following:

> Sep  4 17:56:54 caduceus kernel: [17182814.080000] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission


Further info (unsure what will help here) is when I do **dmesg | grep 1394**

> [17182814.080000] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[17182814.760000] ieee1394: Error parsing configrom for node 0-00:1023
[17182815.440000] ieee1394: Error parsing configrom for node 0-01:1023
[17182816.460000] ieee1394: Error parsing configrom for node 0-00:1023
[17182816.460000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17182816.460000] ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[394fc0002d8420a1]
 

I'm using a **Dell Inspiron 5150** and the System Information (hardinfo) provides: **Texas Instruments PCI4510 IEEE 1394**

gscanbus will find my Panasonic PV-GS180 and sometimes actually say that is what it is (however it is incredibly slow and my machine near locks up at this point)

What else have I tried? Let's see...

Here is **lsmod | grep 1394**
> 
video1394              20300  0
raw1394                30956  0
ohci1394               35124  1 video1394
ieee1394              299832  3 video1394,raw1394,ohci1394


I suppose that's about all I've gotten. If anyone has any thoughts whatsoever, I'd greatly appreciate it.

Thank you!

---

### Post by Bagnaj97 on 2006-10-02
> **endura29 said:**
> 
I'm using a **Dell Inspiron 5150**

My friend has an inspiron 5150 and sudo modprobe raw1394 followed by sudo chmod 777 /dev/raw1394 fixed it. If you add a line saying raw1394 to /etc/modules then the module loads at startup but you still have to use sudo chmod 777 /dev/raw1394 every time.

---

### Post by heyheyhey on 2006-11-16
I've just tried Kino and it has the the module not loaded at the bottom. but if I run the line that is at the top of this thread but get a module not loaded return:

theowner@theowner-laptop:~$ sudo chmod 777 /dev/raw1394
Password:
chmod: cannot access `/dev/raw1394': No such file or directory
theowner@theowner-laptop:~$


Any guesses? 

Cheers Josh

---

### Post by ColinG on 2006-11-17
try doing first, as root:
modprobe dv1394
modprobe raw1394

Also did you do the chmod command as root?

---

### Post by heyheyhey on 2006-11-22
I tried all this from the root terminal and now Kino says there is no AV/c complient cam connected or not switched on?

Anything for that one?

](*,)

---

