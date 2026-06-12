---
title: "Can't resize dock 12.04 LTS x64"
date: 2012-09-13
forum: Desktop Environments
---

### Post by jay87 on 2012-09-13
Hi All

I am running Ubuntu 12.04LTS x64 on a Sony Vaio 17" Laptop.  I am loving it, but have one problem that is frustrating me, which I was hoping you could help with

I like a tiny dock, and I updated Ubuntu, restarted and now can't resize my dock beyond huge!  By default it is now huge.  I had installed compizconfig for a 3D desktop cube switching, but have just noticed this too has disappeared now.  I uninstalled compiz in the hope this would fix things but it hasn't  

In appearence, there is no option to resize the dock any more.  

Any ideas?  

Thanks in advance

Jake

---

### Post by MG&amp;TL on 2012-09-13
What's likely to have happened is that for some reason the update broke your graphics driver (which means fallback graphics). I have a VAIO as well, and that's never happened for me, but there's always a first time.

Can you post your hardware specifications?

---

### Post by jay87 on 2012-09-13
Sure thanks 

           	   **Specifications for VPCEF2E1E/WI**

   **Operating System**

   Operating SystemGenuine Windows® 7 Home Premium (64-bit)        **Architecture**

   ChipsetAMD M880G Chipset   **Colour**

   Cover colourWhite   **CPU**

   Processor NameAMD Athlon™ II Dual-Core Processor P320   Processor Speed (GHz)2.1   L2/L3 Cache (MB)1   Frontside Bus (MHz)3200MHz HyperTransport™ 3.0   Number of Cores2   **Memory**

   Memory Size (GB)4   Memory SpecificationPC3-8500   Memory Speed (MHz)1066   Memory TypeDDR3 SDRAM   Max. Supported Memory (GB)8   **Drives**

   Hard Drive TypeSerial ATA   Hard Drive Capacity (GB)320   Hard Drive Speed (rpm)5400   Optical Drive TypeDVD±RW/±R DL/RAM   **Drives Speed**

   ReadCD x24, CD-R x24, CD-RW x24, DVD x8, DVD-R DL x8, DVD-R x8, DVD-RW x8, DVD+R DL x8, DVD+R x8, DVD+RW x8, DVD-RAM x5   WriteCD-R x24, CD-RW x10, DVD-R DL x6, DVD-R x8, DVD-RW x6, DVD+R DL x6, DVD+R x8, DVD+RW x8, DVD-RAM x5   **Screen**

   Diagonal Size (in)17.3   Diagonal Size (cm)43.8   Aspect Ratio16:9   Resolution1600 x 900   **Graphics**

   Graphic Card NameATI Mobility Radeon™ HD 4250 Graphics   Total Graphics Memory1910MB*   Comments*  Total Available Graphics Memory refers to the classification  of graphics memory, which varies depending on the operating condition,  version of device driver and system memory size.   **Interfaces**

   USB Port (quantity)4   USB Version2.0   USB Connector TypeA   Memory Stick™ Slot1: 4bit M.S. PRO (Duo Only)   Microphone Jack1: Stereo Mini Jack   Headphone Jack1: Stereo Mini Jack   SD Card SlotYES   HDMI OutputYES   VGA Output1: mini D-sub 15p   **Network Connectivity**

   Ethernet (RJ-45 Direct Port)YES   Ethernet Type10Base-T/100Base-TX/1000Base-T   Wireless LANYES   Wireless LAN Type802.11 b/g/n   Wireless LAN Max. Date Rate (Mbps)150 (RX)/150 (TX)   **Audio**

   Built-in SpeakersStereo   Built-in MicrophoneYes: Monaural   Dolby CodecDolby Home Theater v3   **Built-in Camera**

   SpecificationMOTION EYE®   Effective Pixels640x480   Image Sensor (Mega Pixels)0.3   **Keyboard**

   Stroke (mm)2.0   Key Pitch (mm)19.05   Touch PadYES   **Other Features**

   Special ButtonsAssist   Kensigton LockYES   **Software**

   AudioMusic Station   Home NetworkVAIO Media Plus   MultimediaMedia Gallery   MicrosoftInternet Explorer 8, Windows Live Essentials Suite   Office ApplicationAdobe® Reader® 9, Microsoft® Office Starter 2010   OtherVAIO Care, Google Chrome Browser   Photo/VideoPMB VAIO Edition   Security & Backup   Solution PortalVAIO Gate   SONY ToolsRemote Play with PlayStation 3   UtilitiesVAIO Transfer Support, VAIO Update, VAIO Smart network   **Supplied Accesories**

   AC AdaptorVGP-AC19V48   BatteryYES   **Dimensions**

   Depth Main Unit (mm)274   Height Main Unit (mm)32.8-38.0   Width Main Unit (mm)409.1   Weight with Supplied Battery (Kg)3.1   **Primary Battery**

   Model NameVGP-BPS22   Battery TypeLi-Ion (Samsung cell)   Power39Wh (11.1V/3500mAh)   Weight (g)310   Battery Life time (hours)3   Battery Charge time (hours)3.5   Battery Life DisclaimerActual battery life will vary depending on your specific hardware and software configurations. Benchmark: MobileMark 2007 
                       
                                                                              [B]
[/B]

---

### Post by MG&amp;TL on 2012-09-13
Whoah...link next time might be better. :D
 
I see from
 
> Graphic Card NameATI Mobility Radeon™ HD 4250
 
that you've got an ATI card. I've got an Intel one, so I'm not really familiar with the driver process for ATI/AMD cards. Have you tried going to "Additional drivers" and installing whatever it suggests, or if you've already done that, remove it and install it again.
 
Silly little thing, but I think sometimes a new kernel breaks drivers and such.

---

### Post by jay87 on 2012-09-13
Thanks that worked!

Reinstalled and activated the ATI driver and now i have 3D and a small dock again :-)

---

### Post by MG&amp;TL on 2012-09-13
> **jay87 said:**
> thanks that worked!
 
Reinstalled and activated the ati driver and now i have 3d and a small dock again :-)
 
Great! Enjoy your Ubuntu. :)

---

