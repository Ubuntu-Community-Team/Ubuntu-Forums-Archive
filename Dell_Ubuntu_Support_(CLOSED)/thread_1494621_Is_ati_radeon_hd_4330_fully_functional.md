---
title: "Is ati radeon hd 4330 fully functional?"
date: 2010-05-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by barna on 2010-05-27
Hi,

I am about to decide between two notebooks, namely the Toshiba Tecra A11-10D (Intel GMA HD) and the Dell Inspiron 1564 (ATI Radeon HD4330). Before I make the decision, I would like to know which of the two graphics cards are functional under linux (learning from the bad experience with my now-5-years-old Toshiba Satellite, with an ATI Radeon Mobility 7000 IGP graphics card: it was perfectly working with ATI's proprietary driver fglrx, but recent versions of this driver did not anymore support this card, so the open-source driver was used, which for a long period did not support 3D of this card - now it does, but my notebook is now dieing)

Browsing the web I could not get a clear impression about this question. Could anybody comment on this? Also about the graphics card performance. For my professional work I use CAD applications, in my private life I do some amateur video- and picture-editing.

Thanks
Daniel

---

### Post by waynefoutz on 2010-05-27
> **barna said:**
> Hi,

I am about to decide between two notebooks, namely the Toshiba Tecra A11-10D (Intel GMA HD) and the Dell Inspiron 1564 (ATI Radeon HD4330). Before I make the decision, I would like to know which of the two graphics cards are functional under linux (learning from the bad experience with my now-5-years-old Toshiba Satellite, with an ATI Radeon Mobility 7000 IGP graphics card: it was perfectly working with ATI's proprietary driver fglrx, but recent versions of this driver did not anymore support this card, so the open-source driver was used, which for a long period did not support 3D of this card - now it does, but my notebook is now dieing)

Browsing the web I could not get a clear impression about this question. Could anybody comment on this? Also about the graphics card performance. For my professional work I use CAD applications, in my private life I do some amateur video- and picture-editing.

Thanks
Daniel

Stay away from ATI in a laptop. It may be working now, but ATI drops it's support early in the laptop's life. My year and a half old Dell laptop with an ATI cannot run any Ubuntu version newer than Intrepid and have fully functioning 3d. the newer fglrx drivers don't work, the newer xserver Ubuntu uses can't use the older driver. So I'm stuck with Hardy or Debian stable. If i want to use a modern distro I have to use the open source drivers, which are fine for most people, but if you do anything graphic intensive it just doesn't cut it. 

As far as I'm concerned ATI is fine in a desktop where it's only a matter of ripping out the card and replacing it with a new one, but when ATI abandons your laptop graphics card, you're stuck.

---

### Post by barna on 2010-05-27
Yes, I had the same problem, as I described. With Ubuntu 9.10 and the open-source driver,3D did not work (in fact, many applications, like a video player, or skype video, crashed). with 10.04 it seems to work with the open-source driver, but I believe you that this is not as good as the proprietary drivers. 

But then what should I use? I have read in some forum that ATI is trying to be the leading company on the linux segment - does it not mean that there is going to be a change, and there will be better support? Is the open-source driver not catching up with the proprietary one? And anyway, do other companies not have the same problem? 

Thanks.
D

---

### Post by reiki on 2010-05-27
I have an HD4330 in mt Dell Zino HD. It works fine out of the box using the Ubuntu 10.04 LTS. I did not install the proprietary drivers as there was no need. I have full desktop effects turned on. No issues.

---

### Post by barna on 2010-05-28
Hi,
That's a great news, thanks. In the meantime I found this test result:
[http://www.phoronix.com/scan.php?page=article&item=intel_atom_ionamd&num=2](http://www.phoronix.com/scan.php?page=article&item=intel_atom_ionamd&num=2)
which claims 
> 
Starting with the World of Padman game, with all five resolutions tested the NVIDIA ION sharply outperformed the Radeon HD 4330. However, the Radeon HD 4330 was using the ill-optimized open-source Mesa driver stack while the ION was running with NVIDIA's proprietary but very powerful graphics driver.
The open-source Nouveau Gallium3D driver is not in a shape for OpenGL testing right now in Ubuntu 10.04 nor is it used by default and on the ATI Radeon side, we could not use its proprietary Catalyst driver, as the public driver is not yet compatible with X.Org Server 1.7 that's used by Ubuntu 10.04

Since I will anyway need to run my most serious 3D application (Autodesk Inventor) under Windows, I am kind of happy if the card works at all under linux, and I can play videos, make skype video call without crash (which was the case with my current notebook and the open-source driver)

Thanks

---

### Post by luisg on 2010-05-28
I have an Inspiron 14, ati hd4330. You can see [my report here]("http://ubuntuforums.org/showthread.php?t=1409132"), but in short karmic worked great, but found some problems with Lucid.

---

### Post by barna on 2010-05-29
Thanks, it seems very encouraging. What are the problems with lucid?

---

### Post by waynefoutz on 2010-05-29
My ATI card, a Radeon Mobility x1270, had no 3d at all when I was running Jaunty. Karmic got some of it working, Lucid is about 90%. If you don't do anything graphic intensive, the open source drivers are fine. I can't get Google Earth to work, ditto for most of the games. Thee games that do run, the frame rate is pretty bad.
When running Hardy or Intrepid with the proprietary fglrx drivers, I get better frame rates, even when I run the same game or Google Earth in Windows. I'm running Hardy now, and that's probably where I'll stay until next year until the end of life date. The last year  I've seen significant improvements on the open source drivers, so I know they are working on them. Still if I had to do it all over, I would have bought a laptop with an  Nvidia or Intel GPU.

---

