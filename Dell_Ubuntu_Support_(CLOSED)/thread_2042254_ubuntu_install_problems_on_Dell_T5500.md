---
title: "ubuntu install problems on Dell T5500"
date: 2012-08-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hejhoppsan on 2012-08-14
Hi, 

I recently bought a Dell T5500 without any OS on it, and I am trying to install ubuntu using a cd. However, the installation process stops just after I select the language. The error message is: ata_id[312]: HDIO_GET_IDENTITY failed for 'dev/sda': Invalid argument. 

Can anyone tell me what this might mean and how it can be fixed? I tried both the 32-bit and 64-bit ubuntu, and I checked the disk after copying using winMd55Sum. 

The computer is a Dell T5500 with an Intel Xeon E5-2643 processor, a 256GB 2.5inch Serial ATA Solid State Drive, two additional harddrives, HDD Configuration : C3 SATA / SSD 2.5inch, 3-4 Hard Drives, and a 1 GB NVIDIA Quadro 2000 graphics card. 

Any input would be much appreciated as I am pretty much clueless as to what to try.

---

### Post by jregele on 2012-08-25
I'm running into the same problem with a brand new Dell T5600. From what I have found all over the web, it appears to be an issue with the PERC H310 raid controller. The Ubuntu install CD may not have the drivers for this controller.

I can install Redhat 6.3 fine, but after a few days of frustration, the whole reason I moved to Ubuntu in the first place, I want to get Ubuntu to work. The previous install version I tried was 12.04. I just found version 12.04.1 hoping that Ubuntu included the driver in the latest release, but alas, I still get the same error.

I haven't found any conclusive evidence yet that it is the PERC controller just yet. I'm going to plug my hard drive directly into one of the open SATA ports and try to bypass the PERC controller altogether. I'll let you know what I find.

---

### Post by jregele on 2012-08-25
So I connected my hard drive via the second SATA port and took out the raid controller. When I did this, I no longer received the error 
> HDIO_GET_IDENTITY failed for '/dev/sda': Invalid argument
However, nothing else happened beyond that. It just hangs endlessly with a blank screen and a cursor blinking. I tried this with both the 32bit and 64 bit 12.04.1 versions and got the same result.

Then I decided to install the not yet released [Ubuntu 12.10 (Quantal Quetzal) Daily Build]("http://cdimage.ubuntu.com/daily/current/") (downloaded Aug. 25th 2012). I have successfully installed version 12.10 both with and without the PERC controller. 

It does seem to have some bugs with it. It wants to report the bugs fairly often. Somewhere between 12.04.1 and the current daily build they have made changes that will make version 12.10 work on these computers. The big question for now is whether or not it will be stable enough to work with until the official stable release occurs.

---

### Post by jregele on 2012-09-10
So the 12.10 version was too buggy so I went back to work on the 12.04. It turns out that the video card in my computer nvidia quadro 4000 is not on the list of x.org supported cards. So when you boot from the cd you get a blinking cursor even though it sounds like the cd is loading.

I was able to install by replacing the unsupported card with a supported graphics card from an oder computer. In installed 12.04 just fine. I installed the nvidia drivers, put the new quadro 4000 card back in and it booted fine.

Also note that my computer came with a Raid controller that was not supported by the install CD. to get around that I removed it and plugged my single hard drive directly into an available sata port. If you need raid I'm not sure what you can do.

---

### Post by kmpang on 2012-10-12
Dear all,

I'm trying to install Ubuntu 11.10 on a Dell Precision T3600 now. Even the installation is successful, I got this error after I reboot:

ata_id[318]: HDIO_GET_IDENTITY failed for '/dev/sda': Invalid argument

Can you please kindly advise regarding to this problem? 

Thanks in advance.

Regards,
Kar.

---

### Post by kmpang on 2012-10-12
> **jregele said:**
> So the 12.10 version was too buggy so I went back to work on the 12.04. It turns out that the video card in my computer nvidia quadro 4000 is not on the list of x.org supported cards. So when you boot from the cd you get a blinking cursor even though it sounds like the cd is loading.

I was able to install by replacing the unsupported card with a supported graphics card from an oder computer. In installed 12.04 just fine. I installed the nvidia drivers, put the new quadro 4000 card back in and it booted fine.

Also note that my computer came with a Raid controller that was not supported by the install CD. to get around that I removed it and plugged my single hard drive directly into an available sata port. If you need raid I'm not sure what you can do.


Hi, do you actually mean Ubuntu 12.04.1 LTS actually works with T5600?

Please advise.

Thanks.

Kar.

---

