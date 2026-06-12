---
title: "Dell Vostro 1000 RAM problem"
date: 2010-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by d_fiumano on 2010-08-04
Heyo! I need a little help. I have a Dell Vostro 1000 and this is my setup: 

Ubuntu 9.10 (karmic)   {I **think** it's 64bit}
Kernel Linux 2.6.31-22-generic
GNOME 2.28.1

I recently upgraded my RAM from 2gb to 4gb but for some reason, my system only recognises **2.6**gb out of 4gb. I've been to many forums and none can tell me what's wrong. I've come close, but I get hit with so much technical jargon to make my head spin. Any help will be greatly appreciated. Thank you.

---

### Post by jaakan on 2010-08-04
what does "uname -a" give you?

and what version is your bios?

I have this laptop with 4gb + bios version 2.6.3 + Ubuntu 10.04 x64.

here is mine

```

jaakan@jms1000:~$ sudo dmidecode | more
.....
BIOS Information
	Vendor: Dell Inc.
	Version: 2.6.3    
	Release Date: 12/07/2007
.....
System Information
	Manufacturer: Dell Inc.
	Product Name: Vostro   1000
.....
jaakan@jms1000:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3836       3389        446          0        172       1732
-/+ buffers/cache:       1485       2351
Swap:         1953          4       1949
jaakan@jms1000:~$ uname -a
Linux jms1000 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux


```

---

### Post by d_fiumano on 2010-08-04
Well, here is what I got:
SMBIOS 2.4 present.

Handle 0x0001, DMI type 0, 24 bytes
BIOS Information
    Vendor: Dell Inc.
    Version: 2.6.3    
    Release Date: 12/07/2007
    Address: 0xE5860
    Runtime Size: 108448 bytes
    ROM Size: 1024 kB
    Characteristics:
        PCI is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported

Handle 0x0017, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        enUS
    Currently Installed Language: enUS

root@tumo1983:/home/danny# uname -a
Linux tumo1983 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/Linux
root@tumo1983:/home/danny# 


Hope this means something!

---

### Post by Helkaluin on 2010-08-07
I've checked your BIOS stuff, it should be up-to-date. See: [http://support.dell.com/support/downloads/previousversions.aspx?c=us&l=en&s=gen&SystemID=VOS_N_1000&releaseid=R175498&formatid=-1&deviceid=15246&formatcnt=2&dateid=-1&releasetype=BIOS&servicetag=&typeid=-1&catid=-1&source=-1&libid=1&impid=-1&osl=en&vercnt=4&os=WW1&checkFormat=false](http://support.dell.com/support/downloads/previousversions.aspx?c=us&l=en&s=gen&SystemID=VOS_N_1000&releaseid=R175498&formatid=-1&deviceid=15246&formatcnt=2&dateid=-1&releasetype=BIOS&servicetag=&typeid=-1&catid=-1&source=-1&libid=1&impid=-1&osl=en&vercnt=4&os=WW1&checkFormat=false)

> **d_fiumano said:**
> 
root@tumo1983:/home/danny# uname -a
Linux tumo1983 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/Linux
Notice the 'i686' part. You're running 32bit.

The easiest thing  to try now is to install the PAE kernel. Try the 'linux-generic-pae'  package and boot into that kernel. If, afterwards, a 'free -mt' command  shows something closer to 4GB, then fine. If not, post back again.

---

### Post by d_fiumano on 2010-08-09
Hey! It Worked!! Thanks a heapload!!!

---

### Post by Helkaluin on 2010-08-10
Glad it worked. Do tag this thread as 'solved' so that other users can reference this before asking.

---

