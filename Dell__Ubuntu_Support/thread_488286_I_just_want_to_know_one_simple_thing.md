---
title: "I just want to know one simple thing"
date: 2007-06-30
forum: Dell  Ubuntu Support
---

### Post by JustLikeJsh on 2007-06-30
I want to know if I buy this computer and run Ubuntu 7.04 will it be able to connect to the internet?

Here are the specs for the Dell Inspiron 530

PROCESSOR	Intel® Core&#8482;2 Duo Processor E6320 (4MB L2 Cache,1.86GHz,1066 FSB)	edit
OPERATING SYSTEM	Genuine Windows Vista&#8482; Home Premium	edit
MONITOR	No Monitor	edit
MEMORY	2GB Dual Channel DDR2 SDRAM at 667MHz- 2DIMMs	edit
HARD DRIVE	250GB Serial ATA Hard Drive (7200RPM) w/DataBurst Cache&#8482;	edit
OPTICAL DRIVE	16X DVD+/-RW Drive	edit
VIDEO CARD	256MB NVIDIA GeForce 8600GT-DDR3	edit
SOUND	Integrated 7.1 Channel Audio	edit
KEYBOARD & MOUSE	Dell USB Keyboard and Dell Optical USB Mouse	edit
FLOPPY & MEDIA READER	13 in 1 Media Card Reader	edit
MODEM & WIRELESS	Data/Fax Modem plus 802.11b/g wireless PCI card	edit
My Accessories
SPEAKERS	No speakers (Speakers are required to hear audio from your system)	edit
ANTIVIRUS SOFTWARE	No Security Subscription (30-day trial)	edit
PRODUCTIVITY SOFTWARE	Microsoft Works 8. DOES NOT INCLUDE MS WORD	edit
PHOTO AND MUSIC SOFTWARE	Yahoo! Music Jukebox - Music Player	edit
My Service
WARRANTY AND SERVICE	1 Yr In-Home Service, Parts + Labor - Next Business Day	edit
DATASAFE ONLINE BACKUP	Free 3GB DataSafe Online Backup for 1Year	edit
DIAL-UP INTERNET ACCESS	No ISP requested	edit
ALSO INCLUDED WITH YOUR SYSTEM
Mouse	Mouse included in Wireless, Laser or Bluetooth Package	
Adobe Software	Adobe® Acrobat® Reader 7.0	
Network Interface	Integrated 10/100 Ethernet	
Labels	Windows Vista&#8482; Premium

Please, someone help. If the answer is yes it can the how is it done? Do i need drivers or what? And yes I have been searching and searching all day to figure this out.

Thanks

---

### Post by neptho on 2007-06-30
It depends on how you're wanting to connect; It doesn't specify what modem or wireless card are available; most wireless cards will work with ndiswrapper, or a native driver for the 3945 (as well as there being a beta open source driver for the 4945 and 3945, but are not included, as they are still very new, and are not stable).

The answer: We need more information on what's in the machine before we can tell for sure, but the likihood is that it will work

---

### Post by Bartender on 2007-06-30
Please provide a link to the Dell PC you're looking at.
Dell is offering the 530 pre-installed with Ubuntu
[http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DDCWDAL&s=dhs](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DDCWDAL&s=dhs)
Notice this version comes with no modem.  Prior to the Dell roll-out, I was hoping the Ubuntu Dell's would include an internal modem that worked with Ubuntu but they don't.  :(

If you're looking at the Windows 530, my guess is that if there is a winmodem inside it won't work with Ubuntu.  I'm still crossing my fingers for a Dell with Ubuntu and a functional dial-up modem, but that may take a while.  Maybe when Gutsy comes out, supposedly with better winmodem support?

---

### Post by JustLikeJsh on 2007-06-30
the thing is the computer that you listed above doesnt come with the processor i want. and like you said no wireless. why do you need the link to the computer when it tells you the specs right above. I did put a link up before but it just did the same thing you link did. the computer wasnt built any more because its like it reloaded. Maybe I can make the specs a little more clear. And it  says next to modem and wireless what it uses to connect to the internet. Thats what I really want to know. Will it connect. 

Here are the specs again.

**_PROCESSOR_**-Intel® Core™2 Duo Processor E6320 (4MB L2 Cache,1.86GHz,1066 FSB)
**_OPERATING SYSTEM_**-Genuine Windows Vista™ Home Premium
**_MONITOR_**-No Monitor edit
**_MEMORY_**-2GB Dual Channel DDR2 SDRAM at 667MHz- 2DIMMs 
**_HARD DRIVE_**0-250GB Serial ATA Hard Drive (7200RPM) w/DataBurst Cache™ 
**_OPTICAL DRIVE_**-16X DVD+/-RW Drive 
**_VIDEO CARD_**-256MB NVIDIA GeForce 8600GT-DDR3
**_SOUND_**-Integrated 7.1 Channel Audio edit
**_KEYBOARD & MOUSE_**-Dell USB Keyboard and Dell Optical USB Mouse
**_FLOPPY & MEDIA READER_**-13 in 1 Media Card Reader
**_MODEM & WIRELESS_**-Data/Fax Modem plus 802.11b/g wireless PCI card

If you NEED the link then here it is. [http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&l=en&oc=DDCWDC3&s=dhs](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&l=en&oc=DDCWDC3&s=dhs)

And if anyone can let me know if it would be better to buy a different wireless card seperately that will connect to the internet through Ubuntu then please, let me know. Thanks to everyone.

---

### Post by suuperjan on 2007-06-30
If dell doesn't tell us what chip they use for the modem/wireless card, we can not tell you if this card is gonna be supported under ubuntu. However, i can tell you this: 

-If you want trouble free internet, use a network modem, they alwas work. 
-If you need a dial up, please know that most winmodems (usb) are gonna give you a lot of trouble. buy the pc without the modem, and look for a dial-up modem, that supports linux.
-Same story if you want to go wireless, buy the pc without the wireless card, and buy one later, you know is gonna be supported in ubuntu.

here is a list of wireless cards (green is ok, red, is not ok): [http://linux-wless.passys.nl/query_hostif.php?hostif=PCI](http://linux-wless.passys.nl/query_hostif.php?hostif=PCI)

and here is more info over winmodems: [http://linmodems.org/#chipsets](http://linmodems.org/#chipsets) (but really, if you want to have trouble free internet, go for a network modem)

---

