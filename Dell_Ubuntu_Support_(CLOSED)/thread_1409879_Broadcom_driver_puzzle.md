---
title: "Broadcom driver puzzle"
date: 2010-02-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lz1dsb on 2010-02-18
I saw that there were many posts about the Broadcom wireless chips. So in this thread I just want to share my experience and to check out if anyone else experienced something similar. So here we go:
I've got a Dell Studio 1555 with a BCM4312 wireless chip. After a fresh install (I bought the machine without any other OS) of Ubuntu 9.10 my wireless card wasn't working. So I downloaded the official Broadcom wireless Linux driver from their site: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php), followed every instructions there and the wireless card was up and running in a few minutes. Now here comes the tricky part: with this driver I wasn't able to connect to a meshed network (on some places they call it WDS - Wireless Distribution System, basically a network with a few APs broadcasting on the same channel the same SSID, so you should be able to roam flawlessly between them). Also the wireless card was pretty sloppy and slow in associating to a wireless network, sometimes even unable to associate, even if I'm sure 100% that I know the key. After spending few days reading different threads I decided to try out the easy way. I removed the official driver and activated the one distributed from System->Administration->Hardware Drivers (there it's written that this is an official Broadcom driver, so I expected it to be the same like the one I've downloaded as a source code from their site). I was amazed that this solved the problem, I've tested it the last couple of days and the wireless works even better: no problem with meshed wireless networks, the initial association to the wireless network is faster and smoother... So to sum up my thoughts: Does anybody else experience something like this? Does anybody knows why the two drivers are different, or maybe the way to activate the driver is different from Hardware Driver? Also, do you know if it's possible to get the source of the driver after it's activated? And does anybody know where this driver is placed after the so called "activation"? Please accept my apologies if the description is too long...

Cheers,
Boyan

---

### Post by bobcollard on 2010-02-19
> **lz1dsb said:**
>  Does anybody knows why the two drivers are different, or maybe the way to activate the driver is different from Hardware Driver? 

Cheers,
Boyan
From what I can gather the one you downloaded first is from Broadcom and the second comes from Dell.  The Dell driver has Hardware specific changes in it.  You can get almost the same thing with b43-fwcutter which looks at the hardware and pulls just that part of the drivers it needs.  As to where it is kept, I don't know.

---

### Post by lz1dsb on 2010-02-19
This makes sense. I didn't know that... It's strange that Dell aren't offering this as a download from their Linux support site... I find Ubuntuforums.org more informative than their support site "dedicated" to Linux. 

Cheers,
Boyan

---

### Post by bobcollard on 2010-02-19
> **lz1dsb said:**
> This makes sense. I didn't know that... It's strange that Dell aren't offering this as a download from their Linux support site... I find Ubuntuforums.org more informative than their support site "dedicated" to Linux. 

Cheers,
Boyan
I don't have a machine that was originally Linux Based.  Mine came with Vista.  The first day home I downloaded Ubuntu, burned it to disk and trashed Vista within two hours.  I put the disks away and never turned back.

---

### Post by lz1dsb on 2010-02-20
Well, unfortunately I'm bound to WinXP on my work laptop, as this is the corporate policy. That's why I bought this Dell machine, so that I can use Linux OS on it and nothing else. Linux is the only OS that it ever had ;) I still don't understand though why some manufacturers are so persistent and not publish Linux driver for their equipment, which adds for additional inconvenience to the people who use Linux. And it shouldn't matter to them what OS their customers use, but to sell more products... Anyway that hasn't stopped me though... I believe that the situation will improve in the future (well, maybe not the near future). But whatever happens I can still enjoy using a different and innovative OS...

Regards,
Boyan

---

### Post by bobcollard on 2010-02-20
> **lz1dsb said:**
> Well, unfortunately I'm bound to WinXP on my work laptop, as this is the corporate policy. That's why I bought this Dell machine, so that I can use Linux OS on it and nothing else. Linux is the only OS that it ever had ;) I still don't understand though why some manufacturers are so persistent and not publish Linux driver for their equipment, which adds for additional inconvenience to the people who use Linux. And it shouldn't matter to them what OS their customers use, but to sell more products... Anyway that hasn't stopped me though... I believe that the situation will improve in the future (well, maybe not the near future). But whatever happens I can still enjoy using a different and innovative OS...

Regards,
Boyan
Broadcom Drivers are Proprietary Drivers.  This means they are not a part of the Free operating systems that Linux belongs to.  They can recommend them and give you links to them but they cannot use them in their install disks.  It is a matter of Copyright laws etc.  It's complicated and not so handy as Microsoft who has made deals under the table to get things done.

---

### Post by halj32 on 2010-02-20
Just to let you know that the drivers are on the K/Ubuntu disk
/pool/restricted/b/
b43
/pool/main/b..../n for ndis

---

### Post by bobcollard on 2010-02-20
> **halj32 said:**
> Just to let you know that the drivers are on the K/Ubuntu disk
/pool/restricted/b/
b43
/pool/main/b..../n for ndis
Then why, when you open Hardware drivers, do you have to download them with a live feed to get them to work?

---

### Post by lz1dsb on 2010-02-23
So it's still not clear to me: am I able to get this driver as a source code, like the one distributed from the Broadcom's site.

Regards,
Boyan

---

### Post by bobcollard on 2010-02-23
> **lz1dsb said:**
> So it's still not clear to me: am I able to get this driver as a source code, like the one distributed from the Broadcom's site.

Regards,
Boyan
Yes and from what I understand you must choose either 32bit or 64 bit versions to compile.  See screenshot from their site.

---

### Post by lz1dsb on 2010-02-23
That's correct. I've already used that driver, but I had some nasty problems with it though. My question is about the driver that is distributed through Ubuntu Karmic, and is activated from System->Administration->Hardware Support. Can I get this driver as a source?

Cheers,
Boyan

---

### Post by bobcollard on 2010-02-23
> **lz1dsb said:**
> That's correct. I've already used that driver, but I had some nasty problems with it though. My question is about the driver that is distributed through Ubuntu Karmic, and is activated from System->Administration->Hardware Support. Can I get this driver as a source?

Cheers,
Boyan
I don't know exactly where it comes from.  It is already compiled using your hardware configuration or it would not work.  I suspect it comes from Dell, not Ubuntu or Broadcom.  When the installer configures your hardware, the information is gathered then.  The download and install is a three step process if you watch the progress bar.  It looks like Download - Compile - Install.  The bar stops at 50% and  75%.

---

### Post by lz1dsb on 2010-02-24
Yep, I noticed that on the status bar also. Well anyway, I have to live with that for now. The reason I was asking this is because on that driver channel 12 is not supported. So I was thinking if I have the source code to modify it just a little bit in order to support channel 12, or even also 13 and 14. Because in my neighborhood it's pretty noisy in the 2.4GHz spectrum...
In the README from the Broadcom site where I first downloaded the driver from, it's written that they decided not to support channel 12 in order to be compliant with the spectrum rules around the world. I respect that, but since I bought their equipment, wouldn't it be better to leave me a chance to select which channels will be supported on the device when installing the driver? Then it will be my responsibility... Anyway, we're not living in a perfect world.

Cheers, 
Boyan

---

### Post by bobcollard on 2010-02-24
How True!

---

