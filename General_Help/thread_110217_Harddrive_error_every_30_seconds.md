---
title: "Harddrive error every 30 seconds"
date: 2005-12-30
forum: General Help
---

### Post by Frizl on 2005-12-30
After installing and booting for the first time, the system and spits out every thirty seconds a new line of:

"[83.437089] ata1: command 0x25 timeout, stat 0x50 host_stat 24
[113.410799] ata1: command 0x25 timeout, stat 0x50 host_stat 24"

I use a SATA harddrive Maxtor 250GB in an AMD64 system, also installed the 64 bit version of Ubuntu 5.10. My motherboard is an nForce 410 with integrated graphics - ASUS A8N-VM.

Can anybody tell me what's wrong. The system is brand new, I checked the SATA cable - it's well connected.

---

### Post by iceburg on 2006-01-09
I'm having the same issue!  If anyone has any ideas, please help!  My mobo is an MSI K8NGM2-FID with the Nforce 6150/430 chipset.  Ubuntu was running fine, then this just started one day after an apt-get upgrade.  I don't remember all the packages that were updated, but the kernel image was one of them.  I think it may be a linux issue (as opposed to an Ubuntu issue) as I tried to boot with a standard debian boot disk and with the latest gentoo stage3 boot disk and they also both failed during disk access (at the format stage for the drive).  BTW, my disk is a Hitachi Deskstar 250G SATA2 drive.  This is frustrating since all was working well before the update.  I even tried to re-install Ubuntu from the original install disk and it fails as well.  Grrrr.  Back to working on it.

---

### Post by iceburg on 2006-01-19
I updated the system bios and it seems to be working much better now.  I updated to flight 3 of Dapper, and I haven't had any more timeouts.  Graphics performance is poorer than before, but that could be from running dapper.

---

### Post by John.Michael.Kane on 2006-05-03
@iceburg do you have this board fully working network everything?

---

### Post by spockrock on 2006-05-03
I had the same problem but it was in windows I would get really bad drive performance, it was noticable listening ot music, or watching videos.......the problem is simply that the nforce4 controllers and maxtor diamond max10 drives do not work well with each other.  It took me along time to trouble shoot and buying a new drive to fix the problem.  Updating the drives firmware may help, I found on my board if I used the marvel lan port instead of the nvidia port the drive performed better, however in dapper drake I didnt have problems when using either port.  ummm...... basically that maxtor drive now is just a large storage drive from files, and isos that I wouldnt notice a performance hit, like skipping video or skipping audio.  Oh and if I used ps/2 ports instead of the usb the drive had performed poorer.  You can try that to see if that helps but yeah maxtor and nforce 4's dont work well

---

### Post by John.Michael.Kane on 2006-05-04
spockrock so you have this board working with ubuntu, and theres no issues with the  networking? i have read many posts on other forums where theres an issue with the networking chip, and having to compile a new kernel to get this board to work.

---

### Post by spockrock on 2006-05-05
I am running a dfi lanparty ultra-d which uses the nforce4 ultra-d chipset, the board uses the nvidia gigabit and marvells gigabit controllers, I have had both working with dapper drake no problems.  Not the board in question I am sorry...

---

