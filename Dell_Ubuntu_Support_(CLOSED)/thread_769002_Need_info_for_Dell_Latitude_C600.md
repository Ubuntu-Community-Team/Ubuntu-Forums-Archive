---
title: "Need info for Dell Latitude C600"
date: 2008-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RetiredInMaine on 2008-04-26
MY daughter gave me a Dell latitude C600 that has a broken cd reader and I have no way to boot except from the hard drive. The system has Windows 2000 loaded on it.

 It has one usb port. Does anyone know if this is a usb 1 or 2 port? 
(I tried the Dell web site but was unable to find any relevant info.)

Does anyone know if I put a usb cd reader on this port if the system will boot from it? 

Is there any way to load Linux on this system over the net while the system is up and running windows? 

Thanks in advance for any help.

---

### Post by Alehbye on 2008-04-26
The one USB port on this system is USB 1.0. I cannot confirm that you will be able to boot from a USB device, but it's worth a shot if you have a USB drive around. If it doesn't work at first, try removing the modular optical drive from the system and then trying again. (There is a release latch on the bottom of the system that you can use to eject the CD/DVD-ROM drive). 

As for loading it over the net while the system is in Windows, I don't think so unless you use Wubi. 

I hope this info helps.

---

### Post by elquesopicante on 2008-04-26
Firstly, that's a good serviceable laptop there, and you should be able to pick up a replacement CD-ROM drive online for under $30. I got a new-in-box DVD drive for mine for $60, so shop around and find what you need.

Meantime, to answer your questions, the USB port is USB 1.0. I do not know of any way to install Linux via the net while running Windows, sorry.

-Chz

---

### Post by CREEPING DEATH on 2008-04-26
Check ebay, CD-ROMs are easily replaced on those older Dells and not too expensive.
Define "broken", if it's unreliable you might be able to use one of the [minimal disks]("https://help.ubuntu.com/community/Installation/MinimalCD") to install Ubuntu.
Alternatively, there is [Goodbye Microsoft]("http://goodbye-microsoft.com/"), which will load Debian, **without loading a CD-ROM!**

CD

---

### Post by RetiredInMaine on 2008-04-26
Thank you one and all for responding so quickly. I don't thnk an external usb cd/dvd drive works with usb 1, I'll have to check before I buy one. But replacing the internal drive is an option I did not consider. My daughter was quoted $150 to replace it and I don't want to put that much into it. But if I can find one for $50 or so I'll go for it.

Thanks again.

---

### Post by Alehbye on 2008-04-27
You can get a refurbed drive from Dell:

[http://accessories.us.dell.com/sna/category.aspx?c=us&category_id=6991&cs=19&l=en&s=dhs&mfgpid=121749&chassisid=8484&~ck=anav](http://accessories.us.dell.com/sna/category.aspx?c=us&category_id=6991&cs=19&l=en&s=dhs&mfgpid=121749&chassisid=8484&~ck=anav)

They run between $50 - 80, you can probably find them cheaper on eBay, but it's an option. :)

---

### Post by Fly135s on 2008-05-01
Pick one up on eBay cheap, less than $50.

On another note, anybody know how to get Ubuntu 8.04 to increase the screen resolution above 800x600 on my C600?  I have a dual boot with XP which shows the video card as ATI Mobility 128 AGP 2X (DELL) and I can run the screen at 1024x768 there.  I'm new to Ubuntu so take it easy.  Thanks.

---

### Post by Fly135s on 2008-05-02
> **Fly135s said:**
> On another note, anybody know how to get Ubuntu 8.04 to increase the screen resolution above 800x600 on my C600?  I have a dual boot with XP which shows the video card as ATI Mobility 128 AGP 2X (DELL) and I can run the screen at 1024x768 there.  I'm new to Ubuntu so take it easy.  Thanks.

Nevermind, I got it working by fidling with xorg.conf and following some of the steps in the "Ubuntu Hardy Installation Guide" for ATI drivers at cchtml.com.  Basically screwing up xorg.conf drivers forced Ubuntu into low res graphics mode when I rebooted which then gave me the option of manually configuring the system.  I was able to select the Dell Laptop LCD 1024x768 and the ATI Rage 128 driver.  Probably a bassackwards way to get there, but hey, I'm a noob to Ubuntu and Linux.

---

