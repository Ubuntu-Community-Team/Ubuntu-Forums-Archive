---
title: "Downgrading BIOS from A04 to A00 using Ubuntu"
date: 2009-04-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drmank on 2009-04-20
By drmank in Linux

Would anyone be able to tell me how to downgrade the BIOS from A04 to A00 while using Ubuntu 8.10? I have instructions as to how to do it from... 
[http://bigbrovar.wordpress.com/2008/12/](http://bigbrovar.wordpress.com/2008/12/) ... on-ubuntu/


My systemid is: 0x02B0

Visiting the page... 
[http://linux.dell.com/repo/firmware/bios-hdrs/](http://linux.dell.com/repo/firmware/bios-hdrs/)

I could not find the version for my system ID

Can anyone help please? 

Thank you. 

drmank

---

### Post by anjilslaire on 2009-04-20
What system do you have? Vostro? Inspiron? Mini 9? What model? 1420? 1515?

---

### Post by drmank on 2009-04-20
I appologize that I forgot to mention... I have a Dell Mini 9 with Ubuntu 8.10 installed.

---

### Post by anjilslaire on 2009-04-21
Well then, that would be
[http://ftp.us.dell.com/bios/910_A00_BIOS.zip](http://ftp.us.dell.com/bios/910_A00_BIOS.zip)

I recommend getting a DOS-bootable flash drive, placing the files on it, then boot to the DOS environment from the usb & running the bios flasher.

---

### Post by drmank on 2009-04-21
I am a little new to DOS and Ubuntu, and so I am hoping that you could help me out... How do you know if a USB is dos-bootable? Is there a tutorial that you can lead to me to?

Also, do you know if I could use WINE with the .exe file on dell's site... [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R195330&SystemID=INSPIRON910&servicetag=&os=BIOSA&osl=en&deviceid=18840&devlib=0&typecnt=0&vercnt=6&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=269997#3DOS](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R195330&SystemID=INSPIRON910&servicetag=&os=BIOSA&osl=en&deviceid=18840&devlib=0&typecnt=0&vercnt=6&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=269997#3DOS) .... to perform the downgrade?

Thank you in advance.

drmank

---

### Post by anjilslaire on 2009-04-21
I doubt WINE will work to perform the downgrade. You need to make a usb disk bootable; they don;'t come that way.

If you have access to a Windows machine, for simpilicty's sake I strongly recommend using Windows to create a USB flash drive with this tool by HP:
HP USB Disk Format Tool. You can find it here, along with instructions:
[http://www.bay-wolf.com/usbmemstick.htm](http://www.bay-wolf.com/usbmemstick.htm)

After you have it formatted and bootable to DOS, just put the bios files in a folder on flash drive, reboot the mini to the usb stick (on the Dell logo screen, press 0 until you get a screen that lists the devices connected, and select the usb drive)

Once in DOS, you should be able to run the flasher as needed.

Why are you wanting to go back to A00, by the way? I just upgraded to A05, and it works great :)

---

### Post by drmank on 2009-04-21
I want to downgrade because I ordered an 8 cell battery that will give me about 8.5 hours of battery life. However, the system must be set to BIOS A00 to work and charge properly.

---

### Post by drmank on 2009-04-22
If anyone is interested in reading up on the facts and figures on the 8-cell battery is a discussion of it on the mydellmini.com forums... [http://mydellmini.com/forum/8-cells-%2277wh%22-battery-is-here&#451;-t2250.html](http://mydellmini.com/forum/8-cells-%2277wh%22-battery-is-here&#451;-t2250.html)

---

### Post by Urban Taco on 2010-12-07
I'm trying to go from A09 to A00 and when I run the BIOS flasher O160-A00.EXE from a DOS boot disk it tells me that the system cannot install an older version of BIOS ... 

Is there another way to do this?

---

### Post by cnbiz850 on 2010-12-08
> **Urban Taco said:**
> I'm trying to go from A09 to A00 and when I run the BIOS flasher O160-A00.EXE from a DOS boot disk it tells me that the system cannot install an older version of BIOS ... 

Is there another way to do this?

I have tried that on my Inspiron 6400 from within Ubuntu and that was the message I got.  To upgrade is not a problem.

---

