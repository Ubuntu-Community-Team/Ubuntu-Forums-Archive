---
title: "Latitude E6500 smartcard reader"
date: 2008-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by b4rt on 2008-11-08
Hi,

My Dell Latitude E6500 seems to have a smartcard reader.
I installed the package "smartcard" and a program to read and administer smartcards, but my guess is that there is no driver for, or the smartcard reader is simply not recognised.

Does anyone have any experience with smartcard use in linux?

Thanks in advance,

Bart G.

---

### Post by wirelessben on 2009-05-21
b4rt,

Yes, I got it working in Ubuntu 7 with a different smart card reader, as detailed in [Symbolik's blog]("http://symbolik.wordpress.com/2007/02/25/using-dod-cac-and-smartcard-readers-on-linux/").

But, I'm having problems with my Dell Latitude E6500 also. Running pcsc_scan from a terminal reveals:

SCardListReader: Cannot find a smart card reader. (0x8010002E)
Waiting for the first reader...

Obviously, it's time to look for a driver...

---

### Post by xvolter on 2009-06-03
I also have a Latitude E6500, and have been trying to get the SmartCard working except I can't even get the device recognized by Ubuntu. I don't have Windows installed on my laptop either so I can't tell if it's only in Ubuntu or not.

---

### Post by deewoo on 2010-08-02
See 

[[URL="http://wiki.yobi.be/wiki/Laptop_Dell_Latitude_E6500#.28WIP.29_eSATA"]http://wiki.yobi.be/wiki/Laptop_Dell_Latitude_E6500#.28WIP.29_eSATA]("http://wiki.yobi.be/wiki/Laptop_Dell_Latitude_E6500#.28Partial.29_Smartcard_reader")[/URL]

---

### Post by landtuna on 2010-09-23
> **deewoo said:**
> See 

[[URL="http://wiki.yobi.be/wiki/Laptop_Dell_Latitude_E6500#.28WIP.29_eSATA"]http://wiki.yobi.be/wiki/Laptop_Dell_Latitude_E6500#.28WIP.29_eSATA]("http://wiki.yobi.be/wiki/Laptop_Dell_Latitude_E6500#.28Partial.29_Smartcard_reader")[/URL]

I followed those instructions about adding entries to the  /etc/libccid_Info.plist file and I upgraded the firmware from here:

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R267128&SystemID=LAT_E6500&servicetag=&os=WLH&osl=en&deviceid=21505&devlib=0&typecnt=0&vercnt=6&catid=-1&impid=-1&formatcnt=0&libid=60&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=392801](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R267128&SystemID=LAT_E6500&servicetag=&os=WLH&osl=en&deviceid=21505&devlib=0&typecnt=0&vercnt=6&catid=-1&impid=-1&formatcnt=0&libid=60&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=392801)

(Updating the firmware required extracting the files from inside that .exe (which is really a .zip), formatting my swap partition as FAT32, copying the files there, booting from a FreeDOS disk, and running the batch file from C:, which is actually my swap partition.) I downloaded the cackey library from here:

[https://software.forge.mil/sf/frs/do/viewRelease/projects.community_cac/frs.cackey.0_5_12](https://software.forge.mil/sf/frs/do/viewRelease/projects.community_cac/frs.cackey.0_5_12)

(Sadly, you need to use a CAC to get to that site.) I built cackey from sources and told Firefox to use it with my smart card reader.

Now I can use my CAC to get into CAC-protected sites.

---

