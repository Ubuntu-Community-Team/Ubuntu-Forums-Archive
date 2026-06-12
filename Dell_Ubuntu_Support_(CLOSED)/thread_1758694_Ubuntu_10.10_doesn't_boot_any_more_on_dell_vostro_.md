---
title: "Ubuntu 10.10 doesn't boot any more on dell vostro 3300"
date: 2011-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chah on 2011-05-14
I recently got a Dell Vostro 3300. I had an old USB thumbdrive with Ubuntu 10.10 on it. I was able to boot the machine.

The laptop has a 500GB HDD, originally with 3 partitions:
1) /dev/sda1 looked like a boot partition, about 100MB
2) /dev/sda2 was the C: drive with about 250GB
3) /dev/sda3 was the D: drive having about 200+GB. 

I made images of sda1 and sda2, as well as of the MBR. sda3 was more or less empty. 

I deleted the /dev/sda3 partition using fdisk, and then recreated /dev/sda3 slightly smaller, as well as /dev/sda4 that I was intending to put Ubuntu on. The OS reported some problem re-reading the partition table and said it might not be updated until reboot. So I rebooted the machine. I was very surprised to find that the machine no longer boots!

It drops me to an (initramfs) shell saying: Cannot mount /dev/sda3 on /isodevice.

I don't want it to mount anything, I just want it to boot from the USB thumbdrive

At the moment, I'm downloading 11.04 as I've read that the Dell Vostro 3300 has is certified with 11.04, whereas it needs some additional work with 10.04 and 10.10. But I'm puzzled, does anyone know why my attempt to repartition /dev/sda into 4 partitions is causing the computer to drop to the initramfs limited shell? Since I can't boot the machine, I can't undo what I've done, even though I have backups.

Thanks

---

### Post by DMGrier on 2011-05-15
I have heard with most machines cause of the bios will only support 3 partitions, but I am not sure on that.

---

### Post by chah on 2011-05-16
There was something I had done previously with the USB key that was searching for something on /dev/sda3, which was the cause of my problem.

I also want to add a tip to overcome a different problem that the Dell Vostro 3300 is reported to have: a hot right palm rest. I dug around to find what was under the right palm rest. Dell provides a lot of information about what's inside at:
[http://support.dell.com/support/edocs/systems/vos3300/en/SM/index.htm]("http://support.dell.com/support/edocs/systems/vos3300/en/SM/index.htm"). 

I believe that the HDD is under the right palm rest. One thing you can do to help reduce the heat there is to set the HDD to spin-down with:
```
sudo hdparm -S 4 /dev/sda 
```
Assuming your hard drive is /dev/sda. The parameter to the -S flag is the number of 5 second intervals to wait before spinning down, in this case 20 seconds (more or less, read the man page for details). You should note that you may experience more lag when you want to use the HDD after a spin-down, while you wait for the HDD to spin-up again. However the heating issue is alleviated, and I also noticed that my battery life estimation was also increased.

---

