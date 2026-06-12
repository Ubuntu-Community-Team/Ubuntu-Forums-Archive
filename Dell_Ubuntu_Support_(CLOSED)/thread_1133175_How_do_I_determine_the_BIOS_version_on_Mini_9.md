---
title: "How do I determine the BIOS version on Mini 9?"
date: 2009-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JEBB on 2009-04-22
i just received a refurb Dell Mini 9.  I've seen some posts about upgrading and downgrading The BIOS.  I need to start ahead of that:  How do I determine the BIOS version on my Mini 9?  Thanks.

---

### Post by kerry_s on 2009-04-22
at boot go into the bios, write it down, compare it to whats available on there site.
[http://support.dell.com/support/edocs/systems/ins910/en/sm/bios.htm#wp1084976](http://support.dell.com/support/edocs/systems/ins910/en/sm/bios.htm#wp1084976)

just to let you know, if you screw up a bios update, you can brick your computer, you'll have a nice laptop paper weight.

you might want to look at this: [http://ubuntuforums.org/showthread.php?t=1131372](http://ubuntuforums.org/showthread.php?t=1131372)

---

### Post by Brandon Williams on 2009-04-22
Install smbios-utils, and run smbios-sys-info.

```
$ sudo smbios-sys-info
Libsmbios version:      2.2.13
Product Name:           Inspiron 910
Vendor:                 Dell Inc.
**BIOS Version:           A05**
System ID:              0x02B0
Service Tag:            GMFTWF1
Express Service Code:   36185362525
Asset Tag:              
Property Ownership Tag: 
```

---

### Post by JEBB on 2009-04-23
Brandon, 
There is no smbios-util in the list of programs that comes up with Add/Remove.  Where else would I find it?

---

### Post by anjilslaire on 2009-04-23
Do this:

Power on your Mini, and start pressing 2. When the Dell splash screen appears is when you want to press, but it goes by pretty fast, so start repeatedly pressing early is my suggestion.

This will take you to the BIOS screen, which will show you, among other things:
System Time
System Date
**BIOS Version**

---

### Post by Brandon Williams on 2009-04-23
> **JEBB said:**
> Brandon, 
There is no smbios-util in the list of programs that comes up with Add/Remove.  Where else would I find it?

Sorry ... I didn't realize that smbios-utils is only available in Jaunty. Earlier releases have libsmbios-bin. With that package, you will run getSystemId instead of smbios-sys-info (actually, getSystemId works in Jaunty, too).

---

### Post by Brandon Williams on 2009-04-23
I just encountered another method that will likely work in all releases without installing any new software (I'm only certain that this is true in Jaunty, though).

```
$ sudo dmidecode -s bios-version
A05
```

---

### Post by anjilslaire on 2009-04-24
works in Intrepid as well. I'll be upgrading  to Jaunty this weekend, but my 8.10 Mini 9 shows the bios correctly with the above command. Well done :)

---

### Post by Brandon Williams on 2009-04-24
It's too bad that the other parts of smbios don't work on the mini 9 ... such as the bios flashing utility! The library comes from Dell, but they don't provide the bios in the necessary format to use their utility for flashing from within Linux. This seems like it should be an easy fix for something that has been really frustrating to users who bought the mini 9 with Ubuntu pre-installed. Oh well ... at least I didn't have to pay the Micro$oft tax :-)

---

### Post by anjilslaire on 2009-04-24
The reason Dell won't/hasn't fixed the bios issue for linux is because they don't recommend updating the bios on linux-shipped Mini 9's. They claim there are regressions and th code isn't signed off for linux machines.

Every so often you'll find a rep or dev around here that says updating the bios is not recommended.

---

### Post by Brandon Williams on 2009-04-24
Yes ... but even with that, despite the fact that they claim there are regressions, I haven't heard of anyone who has moved to A04 having any trouble. Not only that, but my mini shipped with the A02 bios, even though the web site said that linux users should not upgrade the bios from A01.

Basically, I think they are only saying that you shouldn't upgrade because they don't want to the necessary work to provide an upgrade path. I don't believe that it is due to actual problems with the BIOS once installed.

Still, your point is well taken. The BIOS can't be upgraded using their tool because they don't support BIOS upgrades on the mini for Linux users.

---

### Post by anjilslaire on 2009-04-24
Oh, I completely agree. I've loaded every bios available so far on my Mini 9, including A05 the day it was released, on top of that I've been running 8.10 since the day I got it back in December. "Dellbuntu" lasted about an hour ;)

Experimenting with 9.04 today.

Zero bios issue so far.

---

### Post by JEBB on 2009-04-24
I used the method Brandon gave.  It showed that I have A04.  Do I need to update the BIOS?  If so what is the best (read easiest) way?  Thanks.

---

### Post by Brandon Williams on 2009-04-24
> **JEBB said:**
> I used the method Brandon gave.  It showed that I have A04.  Do I need to update the BIOS?  If so what is the best (read easiest) way?  Thanks.

When I flashed the A04 bios to my machine, it was because I wanted to see if a VGA fix in the update fixed a problem I was having. It didn't, but a software update eventually did.

If you are not having any trouble that seems related to changes in the A05 bios, then I wouldn't bother flashing the bios. A lot of people who got earlier models that shipped with the A00 bios wanted the A02 or later so that they would have the F11 and F12 mappings that were added in that bios version.

---

