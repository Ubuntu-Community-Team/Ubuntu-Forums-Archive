---
title: "problem with wireless DWL-G650+"
date: 2006-03-13
forum: Desktop Environments
---

### Post by kpaul on 2006-03-13
Hi,
I have problem with my wireless network card D-Link DWL-G650+ 'working'(not working) under kubuntu 5.10 with kernel 2.6.12. on my laptop Toshiba satellite A60.
I use acx100/111 with firmware FwRad16 and acx-20060215 and after test module to work I have:
root@pjk:/usr/src/axc-20060215# insmod ./acx.ko. 
insmod: error inserting './acx.ko': -1 Unknown symbol in module
I also tried with different version acx and firmware and it's the same. 

dmesg
.....
[4295364.118000] acx: Unknown symbol release_firmware
[4295364.118000] acx: Unknown symbol request_firmware

I don't know where is problem, maybe somebody can help me.

I describe how i compiled package acx:
1)download acx and firmware.
2)write firmware into /lib/hotplag/firmware as  tiacx111c16
3)unzip acx in /usr/src/acx-20060215
4)and make -C /lib/modules/`uname -r`/build M=`pwd`
5)insmod ./acx.ko ... and you know what it's next

when i try iwconfig i get:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

There is anybody has some suggestion or help?

Thank You
Regards

Paul

---

### Post by Zelut on 2006-03-13
I would suggest trying ndiswrapper.  Give a forum search for ndiswrapper <your-card> and see what you can find.  I've been using it for wireless support on 5 different wireless cards and it works fine.

---

### Post by kpaul on 2006-03-14
Hi, 
thank you for suggestion I tryed ndiswrapper, but after install and load module i have :
ndiswrapper -l
driver presents



but no hardware present, do you have any sugestion?

Thanks 
Paul

---

### Post by nalmeth on 2006-03-14
I have the same card on my laptop, and I can't get it going at all. There is supposed to be support in the kernel for this, but I believe you have to install the restricted-modules for your kernel, maybe the kernel-headers as well. I think my problem is hardware related, so there's little chance that I'll be able to get mine going. 

Keep posting your progress

---

### Post by kpaul on 2006-03-14
Hi, 
when I try recognize my network card:
sudo cardctl ident
I havent nothing :-(
I get to know that some system my have problem to read memory card so i change /etc/pcmcia/config.opts :
from :
  include memory 0xc0000-0xfffff
  include memory 0xa0000000-0xa0ffffff
  include memory 0x60000000-0x60ffffff

to :

  include memory 0xd0000-0xdffff
  include memory 0xc0000-0xcffff
  include memory 0xc8000-0xcffff
  include memory 0xd8000-0xdffff

but I still haven't see my hadrware.
Maby on your system that will help.
If yes let me know.

regards,
Pawel

---

### Post by kpaul on 2006-03-20
Hi, as I wrote in kubuntu it is a problem with read memory from devices. I have suse 10.0 and that one has a diffrent range of read addres in /etc/pcmcia/config .opts 
When I install my wireless network card on suse 10.0 it wasn't problem to read memory card and card work without problem.

Regards,
Paul

---

### Post by psikor on 2006-04-19
I had the same problem.

Try `setpci -s 0:14.4 subordinate_bus=03`. Worked with me.

---

