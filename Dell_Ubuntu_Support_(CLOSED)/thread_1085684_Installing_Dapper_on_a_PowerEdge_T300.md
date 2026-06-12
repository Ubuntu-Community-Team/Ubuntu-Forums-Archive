---
title: "Installing Dapper on a PowerEdge T300"
date: 2009-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chrislynch8 on 2009-03-03
Hi,

I have installed successfully on two other PowerEdge Servers 1900 and a 2900. I now have a lower spec T300 for small offices I wish to install Ubuntu on.

I remove the pre-configure RAID on the Dell Server and then boot to the CD and select "Install a LAMP Server".

I select the normal settings for me ( English, Ireland, British).

When it starts detecting Hardware it fails on the CD-ROM. I get the following message

[HTML]No common CD-ROM drive was detected

You may need to load additional drivers from a driver floppy. If you have such a floppy available now, put it in the drive, and continue. Other wise, you will be given the option to manually select CD-ROM modules

Load CD-ROM drivers from a floppy? Yes/No options[/HTML]

I select no because I have no floppies, I then get another message saying

[HTML]
No Common CD-ROM drive was detected

Your CD-ROM drive may be an old Mitsumi or another non-IDE, non-SCSI CD-ROM. In that case you should chose which module to load and the device to use. If you don't know which module and device are needed, look for some documentation or try a network install instead of CD-ROm

Manually select a CD-ROM module and device? yes/no options[/HTML]

The CD-ROM drive is in a brand new server. I don't know what options to take etc.

Has anyone had this issue before?

Rgds
Chris

---

### Post by chrislynch8 on 2009-03-04
Hi no Takers.

I have an update and maybe someone can help now. It appears to work fine with 7.10 and. The CD/DVD -ROM is a SATA drive with a connection into the motherboard. Talking to Dell support, they say that the new SATA and motherboard drivers may not be in the Disdro I'm using...

So How can I fine the files I need and slipstream them into my 6.02 install Disk....

Rgds
Chris

---

### Post by notwen on 2009-03-04
Curious why you're using these older versions?  Current version is Ubuntu 8.10 (aka. Intrepid Ibex).  I would at least recommend using [Ubuntu 8.04 LTS (aka. Hardy Heron)]("http://releases.ubuntu.com/8.04/").  [LTS]("https://wiki.ubuntu.com/LTS") stands for long-term support which you would likely want for your server install.

---

### Post by nanog on 2009-03-04
There are threads on this topic in the server section of the forum. 

I found it impossible to install amd64 hardy on this box (the debian and unbiquity installer just dies due to some weird kernel bug). The only solution was to upgrade from 6.06.2. 

My solution: I installed on another box and just plugged in the drive. For the following T300s I just dded the image over and changed the uuid. Worked like a charm. 

Others used unetboot or a usb key to install.

---

### Post by chrislynch8 on 2009-03-05
Thanks for the response

> **notwen said:**
> Curious why you're using these older versions?  Current version is Ubuntu 8.10 (aka. Intrepid Ibex).  I would at least recommend using [Ubuntu 8.04 LTS (aka. Hardy Heron)]("http://releases.ubuntu.com/8.04/").  [LTS]("https://wiki.ubuntu.com/LTS") stands for long-term support which you would likely want for your server install.

I'm in the middle of a roll out so stopping and test a new OS at this moment is not an option, plus I am using 6.06.2 LTS

> **nanog said:**
> There are threads on this topic in the server section of the forum. 

I found it impossible to install amd64 hardy on this box (the debian and unbiquity installer just dies due to some weird kernel bug). The only solution was to upgrade from 6.06.2. 

My solution: I installed on another box and just plugged in the drive. For the following T300s I just dded the image over and changed the uuid. Worked like a charm. 

Others used unetboot or a usb key to install.

This seems to be the case, I was told buy a senior support person in Dell yesterday and that the new SATA CD-ROMs are causing issue for almost all OSes.

Seems I can install fine using a USb key or a USB CD-ROM.. So I'll give this a go. I also have Mondo images of another server I might try that also..

Rgds
Chris

---

