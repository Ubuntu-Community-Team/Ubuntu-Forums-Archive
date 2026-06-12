---
title: "DesktopCD hangs after error message??? Please Help"
date: 2006-08-31
forum: Desktop Environments
---

### Post by erv2 on 2006-08-31
hi, i am a newbie of ubuntu, and a total beginner of linux.

i download the latest desktopCD and run it in my machine, it stops proceding after this error message:

Uncompressing Linux... Ok, booting the kernel.
[17179570.60800] PCI: Cannot allocate resource region 3 of device 0000:05:00.0

here's the spec of my machine:
AMD64 3000+ 
NForce4 
6200 Turbo Cache
Seagate 80G PATA + Seagate 160G SATA
3com 10/100M network card (not the onboard chip)
Creative Audigy sound card

i did take the network card and sound card out, but it still hangs after the error message. 

the booting up is also very slow, it took me about 3-5 min to get to the point where it hangs.(consider my machine isn't the slow type) the machine will still try to read the cd-rom every now and then(about 2-3 mins), but nothing really happens.

has this been asked before, i tried google, someone had this problem before, but they can start up anyway while my machine just hangs there forever.

i tried both 64bit and normal desktopCD, it hangs with the same error message.

any idea? thanks.

---

### Post by erv2 on 2006-09-01
i spent some time on finding the solution on google, but with no luck, the closest i get is link, which claims it's a bug:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/38263](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/38263)

does anyone know how to solve it? thanks.

---

### Post by erv2 on 2006-09-04
nobody knows?

---

### Post by mgmiller on 2006-09-04
Try minimizing the hardware as much as possible.  Try disconnecting both of your hard drives and keep the sound and network cards out.  Basically, just cpu ram and video.  use a ps2 keyboard, usb mouse should be ok, in BIOS, disable legacy USB support.  If it works, try adding in 1 piece of hardware at a time. Especially the hard drives, just add them back one at a time. Make absolutely sure that the jumper settings on your optical drive and PATA hard drive are correct.  Don't rely on cable select, set them to master & slave.  Consider putting the hard drive and optical drive on seperate cables, both jumpered as master (or standalone for western digital drives) It's slow to trouble shoot this way, but at least it gives you a start.  Make sure your ram is good (memtest) and vacuum out all the dustbunnies while you have your case open.

Good Luck.

---

