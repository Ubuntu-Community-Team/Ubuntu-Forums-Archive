---
title: "Upgradding BIOS on Dell Mini 10 (1010)"
date: 2010-01-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pjman on 2010-01-29
Does anyone know how to upgrade the BIOS on a Dell Mini 10 (1010)?

The Ubuntu specific instructions on Dells site say to "Locate the latest BIOS update file for your computer at support.dell.com.". The only downloads I see are exe's for Windows.

[http://support.dell.com/support/edocs/systems/ins1010/en/sm/bios.htm#wp1109918](http://support.dell.com/support/edocs/systems/ins1010/en/sm/bios.htm#wp1109918)

Thank you!

---

### Post by linuxguy2009 on 2010-02-03
Yep Windows only. My best advice is to Clonezilla your machine and install your Windows CD/DVD it came with. Update teh BIOS and then Clonezilla back again. If you dont have a Windows disk then your out of luck.

---

### Post by mikewhatever on 2010-02-03
Here is an interesting page: [http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate).

I am on a mini 10, and the output of getSystemId is as follows:

```
Libsmbios version:      2.2.13
Product Name:           Inspiron 1010
Vendor:                 Dell Inc.
BIOS Version:           A03
System ID:              0x02C6
Service Tag:            FMKMHJ1
Express Service Code:   34016632381
Asset Tag:              **********
Property Ownership Tag: 

```

The procedure looks really easy to follow, however, there wasn't a bios for 0x02C6 system ID.:D

---

### Post by pjman on 2010-04-02
I successfully upgrading my Dell Mini 10 BIOS to A11 using freedos!!

I created a boot usb drive following these instructions (unetbootin freedos wouldn't boot on my Mini 10):

[http://sourceforge.net/apps/mediawiki/freedos/index.php?title=USB](http://sourceforge.net/apps/mediawiki/freedos/index.php?title=USB)

After copying the dos BIOS exe from Dell's site to the USB drive I booted into freedos and ran the executable. Everything seem to be running great.

---

### Post by mikewhatever on 2010-06-13
Guess I was bored today, so I thought looking into upgrading the BIOS on the dell mini 10 was a good idea. There are several BIOS versions for the mini 10, and all of them require Windows. I've tried the latest version at the time of writing, A11, and it wouldn't run on freeDOS. After some digging, it turned out Dell had [_BIOS versions for DOS_](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R220565&SystemID=INSPIRON1010&servicetag=&os=WW1&osl=en&deviceid=19793&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=314149)
Note how it says "Download Type:	BIOS (DOS Version)".
The freedos I used was the one bundled with Clonezilla, since neither Unetbootin's nor the one suggested by pjman above would load. The instructions on how to put Clonezilla on a usb are [_-->here<--_]("http://www.clonezilla.org/clonezilla-live/liveusb.php").
That part was easy, but the following steps had a stumbling stone for me. Clonezilla's freedos has a boot menu of five options. I selected the safe mode, and was then presented with the prompt "A:\>". All efforts to find the 'R220565.EXE' file I had put into the top directory of the usb stick were in vain. All of the following didn't work: [s]'cd c:\', 'cd c', cd 'c:'[/s]. After long last, I found that 'c:' did the trick, and switched me to "C:\>". What's left was to run the executable by typing its name, in my case, R220565.EXE, and waiting through the update. It took about a minute or so and beeped a lot.

---

