---
title: "2nd tv screen Issue"
date: 2011-03-01
forum: Desktop Environments
---

### Post by Corpy on 2011-03-01
Hey all. 

Ok so im new to Ubuntu and not look at it all in depth yet. 

I have a small issue. Im using a Toshiba Satellite A200 Laptop. I installed Ubuntu on it yesterday because i was fed up of windows vista. On windows Vista i use to Plug the laptop into a 50" LG plasma and watch online movies and sports. And for the audio i used a USB cable from the laptop into a Pioneer VSA-AX10Ai Amp. My issue is.I plugged the VGA cable in today to test it on Ubuntu. I went into apps/sys/display and all of a sudden the laptop screen just kept flashing on and off. the Tv was saying in the top left 32" and because of all the flashing i could not do anything so i just turned the laptop off. I have not attempted the Audio Via USB yet . I know vista and my IMAC auto picked up the AMP but not on UBUNTU can anyone help me with the Screen issue ??????

---

### Post by Corpy on 2011-03-01
Anyone have any information all ??? to why the laptop screen starts going mental ????? the sound worked just fine ! when i plugged the USB into the laptop the UBUNTU picked up the Pioneer VSA-AX10Ai so thats fine :-) just want the screen issue sorting :-)

---

### Post by upptown on 2011-03-01
O.K. Gonna need some more information if your gonna get any help:

1) What version of ubuntu are you using?
2) What video chipset does your laptop use? (Nvidia, ATI, Intel?)

I have plugged into my in-law's 50" LG for the last 2 years (9.04 and up) with no problems.

Bit of advice for using the forum:  The more info you provide, the more likely some one will be to help.  Do you know how to do command line input (CLI)?  

If not, try this: main menu-accessories>terminal

Type this into the window that opens and cut and paste the output in your next post:
```
lspci
```

Also, it is expected to wait a day before "bumping" (posting/reposting in your thread to bring it to the top of the queue) or pressing for answers to your issue.  If you have additional info or updates it's ok to post more often.  Otherwise, please be patient.  Once we get some more details from you we can see what to do to help you out.

---

### Post by Corpy on 2011-03-01
Hi Thanks for the Fast reply here is all the information. 

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


Another Thing i noticed with Ubuntu was after the Install i no longer needed the 5ghz Usb Stick the built in Network card started working witch was strange. :-) 

but yeh just the tv issue if you need more information ill happily provide :-) .. And i only download Ubuntu off the site yesterday

Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 thats whats on the CD

2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

---

### Post by Corpy on 2011-03-01
ok Just done some more checks and If i mirror the Image and Apply it work i get the picture on the TV...... BUT it will only do a 1024x768(4:3) ! and i need 1920x1080(16:9) 100Hz :-) and Not on a Mirror Image :-) tv is a LG 50" Full HD Plasma 600Hz if that helps

Oh and also i have a Issue with VEETLE . 

I wanted to watch HD so i downloaded Veetle and installed it via the term and it said install finished. so i opened Firefox back up and went to veetle only to find out i still cant view HD and half the movie channels say this is a HD channel Download VEETLE :-( i have already downloaded and installed it GRRRRRR

---

### Post by Corpy on 2011-03-01
I thought it would help if i gave more information but there is no reply still LOL !! would you like me to post a video of whats going on as well ???????

---

### Post by upptown on 2011-03-02
> **Corpy said:**
> I thought it would help if i gave more information but there is no reply still LOL !! would you like me to post a video of whats going on as well ???????

O.K. please calm down.  I am perfectly willing to try to help but I only check the forums about once a day and yesterday I was not feeling well so I went to be early.  We are a very helpful bunch here but you need some patience.  

Here are some links that should help with veetle:

[HTML]http://www.linuxquestions.org/questions/linux-newbie-8/how-to-get-veetle-working-on-ubuntu-789251/
[/HTML]

[HTML]http://www.techheadz.co.uk/121.html[/HTML]

[HTML]http://ubuntuforums.org/showthread.php?t=1591661&highlight=veetle[/HTML]

Here is a link that should help with your dual screen issue:

[HTML]http://ubuntuforums.org/showthread.php?t=1683179&highlight=intel+943+resolution[/HTML]

Now, I am in no way an expert like many of the helpful guys/gals here but I do know my way around a search engine.  I recommend doing some google searches trying the following key words: **intel 945gm ubuntu 10.10 dual screen** and **veetle ubuntu 10.10**  let me know if this helps

---

