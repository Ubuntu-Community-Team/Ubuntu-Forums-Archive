---
title: "[SOLVED] 5GB Reinstallation ISO - 4.7GB DVD - Help!"
date: 2008-03-10
forum: Dell  Ubuntu Support
---

### Post by treb0r on 2008-03-10
I just took delivery of my nice new Inspiron 530, which I'm trying to get to work with a 17" Protouch Aspect touch screen (Without Success). I have a 3rd party driver that might work, but the author of the driver has asked me to do a clean install of Gutsy before I try the driver.

Knowing that I'd seen a Dell Re-installation ISO image on the desktop, I popped in a blank DVD and tried to burn it. Guess what? The freaking image is too big for the blank disk!! The drive is a standard DVD recorder, and the media is a standard 4.7GB disk. The ISO is 5GB. What's even crazier is that the ISO appears to have less than 2GB of data on it. 

I just called the DELL Ubuntu support line, and they had no idea what to say, or what I should do. I have another image downloading from DELL as I write this, but the idea that DELL are shipping images larger than the included DVD drive can handle seems beyond crazy.

Any ideas? What tools can I use to recreate a smaller ISO file?

---

### Post by Jimmey on 2008-03-10
If you need to do a clean installation of Gutsy, what's wrong with the ~700MB standard .iso?

---

### Post by treb0r on 2008-03-10
Hello Jimmey,

I'll tell you what's wrong with it - it doesn't include all the extra drivers that DELL includes on the custom re-installation ISO, and I need to make sure that the graphics card works properly as this will be a publicly accessible kiosk.

I just want to know how I'm supposed to use the re-installation ISO that came supplied with the computer.

---

### Post by notwen on 2008-03-10
Just curious, which iso did you download?  All of them appear to be around the 4.3 GB size on the [Dell Linux Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO") page.  Try a checksum on your iso and see if it matches up, if not then you need to download it again.  Hope this helps.  =]

>  
Inspiron 1420n 	Intel X3100 	ubuntu-dell-1420n-intelvideo-reinstall.iso 	4312 MB 	e5c861380109d097879c1b8c12f493c9
Inspiron 1420n 	nVidia 8400M GS 	ubuntu-dell-1420n-nvidiavideo-reinstall.iso 	4317 MB 	c65a10b9644f76245851d245a4de3bf8
[B]Inspiron 530n 	nVidia 8400M GS 	ubuntu-dell-530n-nvidiavideo-reinstall.iso 	4313 MB 	6f791a370c461965c557f7998e29f342
Inspiron 530n 	nVidia 8600M GT 	ubuntu-dell-530n-nvidiavideo-reinstall.iso 	4313 MB 	6f791a370c461965c557f7998e29f342[/B]
XPS M1330n 	nVidia 8400M GS 	ubuntu-dell-M1330n-nvidiavideo-reinstall.iso 	4314 MB 	5970597b50dab5834c12376ada1ccede
XPS M1330n 	Intel X3100 	ubuntu-dell-M1330n-intelvideo-reinstall.iso 	4310 MB 	9b0c4e0b68d4c22e69170cc8ae24724e
Inspiron 1525n 	Intel X3100 	ubuntu-dell-1525n-intelvideo-reinstall.iso 	4313 MB 	2ee17c3e98f2a055ef6e2050ce7a9bcf

---

### Post by treb0r on 2008-03-11
Hi Notwen,

I didn't download the ISO - it came with the new computer, sitting on the desktop.

I'm going to have to download one now though as nobody at DELL can tell me how I'm supposed to burn it. It's a crazy old world.

---

### Post by notwen on 2008-03-11
You may be trying to burn the image that is used during a system restore.  My Inspiron 1420n also came w/ a normal Ubuntu LiveCD as well, they ship these standard I believe w/ any Ubuntu pre-loaded system.  While the custom Dell Ubuntu images have come out a month or two after the initial Ubuntu release.  

> I have a 3rd party driver that might work, but the author of the driver has asked me to do a clean install of Gutsy before I try the driver.

If your new desktop is freshly out of the  box I don't see why a clean install would be necessary, but you could also do a system restore by selecting the last option in your GRUB menu, this will wipe the system and set it up exactly as it was when you pulled it out of it's box.  Best of luck to you.

---

### Post by treb0r on 2008-03-11
Hi nowen,

I think you should get a job at DELL Ubuntu support.

You would expect that the DELL people could have told me that on the phone.

You are correct, and its' not such a crazy world after all!

Thanks dude!

treb0r

---

### Post by notwen on 2008-03-11
Very welcome, glad I could be of assistance.  Be sure to post back and update us on your monitor, others may have similar models and might not know whether or not it is possible to use said monitor w/ their system.  =]

---

### Post by treb0r on 2008-03-11
nowen,

The monitor is a real problem. It turns out that the Protouch Aspect monitor is actually manufactured by a company called Aspen, who have been bought out by a Taiwanese company. The website that had the source for the driver is now unavailable. I have found out however that this monitor can be driven successfully by the Idealtek driver, which is actually included in the stock Linux kernel.

I'm now considering compiling a custom kernel that includes the driver. I'm unhappy about 'forking' from the stock Ubuntu install though. Is there another way I could do this? Would it be possible to compile just the kernel module from the kernel source somehow? I used to regularly compile custom kernels when I used Debian, so I'm not too afraid. Any further advice would be much appreciated.

Regards,

treb0r

---

### Post by notwen on 2008-03-11
You would know more than I when it comes to compiling a specific module from within the kernel source.  I haven't found the need to compile my own kernel, nor look for specific modules within said kernel.  What monitor do you have by chance?  A simple Google search has turned up plenty of pages regarding Aspen/Idealtek drivers for Debian/Ubuntu.

---

### Post by treb0r on 2008-03-11
Yes indeed, but all roads lead to a site that is no longer there.

Thanks again for your help!

treb0r

---

### Post by treb0r on 2008-03-18
Just to let everybody know, I finally got the screen working after swapping it for a new one, that also came with an up-to-date driver CD.

If you want a touchscreen that works out of the box with Ubuntu, contact Protouch.

[http://www.protouch.co.uk/](http://www.protouch.co.uk/)

---

### Post by notwen on 2008-03-19
> **treb0r said:**
> Just to let everybody know, I finally got the screen working after swapping it for a new one, that also came with an up-to-date driver CD.

If you want a touchscreen that works out of the box with Ubuntu, contact Protouch.

[http://www.protouch.co.uk/](http://www.protouch.co.uk/)

Glad to hear you were able to get it up & running.  =]

---

