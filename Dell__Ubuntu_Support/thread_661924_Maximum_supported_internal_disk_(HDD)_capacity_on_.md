---
title: "Maximum supported internal disk (HDD) capacity on D820 ?"
date: 2008-01-08
forum: Dell  Ubuntu Support
---

### Post by =JeffH on 2008-01-08
I have a D820 -- I ordered it with the 100GB 7200 rpm drive (HTS721010G9SA00) which has as its interface "ATA/ATAPI-7 T13 1532D revision 1" (according to smartctl)

I've bought several aftermarket drives for this system and my older C610s, but all have been 120GB and less, and ATA-6 interfaces. I usually purchase from newegg.com, and they list available interfaces as ATA-6, SATA 3.0Gb/s, Serial ATA-150.

I'm interested in replacing my 100GB system disk with a 200GB 7200rpm disk (HITACHI Travelstar 7K200 HTS722020K9SA00 (0A50940) 200GB 7200 RPM 16MB Cache Serial ATA150 Notebook Hard Drive) but the only one available is listed as having a "Serial ATA150" interface. Yet one reviewer says "works great in a latitude" (not specifying which latitude of course).

Also, I note that in Wikipedia ([http://en.wikipedia.org/wiki/ATA-6](http://en.wikipedia.org/wiki/ATA-6)), ATA-7 is listed as having a "transfer mode added" of "SATA/150" (listed in the table near the bottom of the page).

So, my questions:

1. which of the above listed interfaces will work with the disk controller embedded in my system's chipset?

2. what's the largest hard disk that the bios & disk controller in the D820 can handle (e.g. 120gb, 160gb, 200gb, 250gb, etc)?

3. do you think the "HITACHI Travelstar 7K200 HTS722020K9SA00 (0A50940) 200GB 7200 RPM 16MB Cache Serial ATA150 Notebook Hard Drive" will work in my D820?

4. what about a 250GB drive in the modular bay? (I currently have a 120GB in there)

thanks,

=JeffH

---

### Post by jmb_no on 2008-01-13
Hi, 

In case this helps you: I installed a 250GB Samsung in my D280 some time before October 2007 and haven't had any problems with it so far. 

According to Windows (not in Ubuntu at the moment, sorry about that), it's a Samsung Spinpoint (HM250JI).  

[http://www.samsung.com/ph/products/harddiskdrive/spinpointm/hm250ji.asp](http://www.samsung.com/ph/products/harddiskdrive/spinpointm/hm250ji.asp)

Cheers,

---

### Post by =JeffH on 2008-01-16
Interesting -- thanks for the info, that's a helpful datapoint. 

You can "see all of the disk" i take it?

=JeffH

---

### Post by =JeffH on 2008-01-17
ah, ok, so see below for info wrt why jmb_no's disk is likely working just fine...

To: [email]ubuntu-users@lists.ubuntu.com[/email]
From: Eberhard Roloff <tuxebi@gmx.de>
Subject: Re: 48-bit LBA enhancement to the ATA interface - Hard disk drive
	(HDD)    interface questions
Date: Wed, 16 Jan 2008 20:46:31 +0100

Hi, the potential BIOS ATA ristrictions are a non issue for modern
Operating Systems. This applies to Linux, but to Microsoft, just as well.
All you need it that Linux can recognize "some partition" to boot from,
via the bios. This can be small and within the (say) first 120GBs. ;-))

After this, the OS itself will control any harddisk you might have.

kind regards
Eberhard

' =JeffH ' wrote:
> Ok, I want/need to figure out how big a HDD I can upgrade to *internally* to 
> on my
> Dell D820 lapstation.
> 
> How does one go about figuring out whether there are any hard and fast 
> restrictions given the internal IDE/ATA disk interface and/or BIOS 
> implementation peculiarities? And/or ubuntu/debian/linux driver limitations?
> 
> I've been told that the limit on this machine is nominally a 120GB disk (on 
> the internal ATA/EIDE disk controller interface). But that might be someone 
> with a Windows focus. I'm running (k)ubuntu 6.10 Edgy.
> 
> Some modest research indicates that this system (e.g. the BIOS) _might_ be 
> subject to the "48-bit LBA" problem/issue, but also that it's possible that 
> the Linux 2.6.* kernel might obviate any issues and I'm all set.
> 
> Without yet buying a > 120GB disk and actually trying it, how do i figure this 
> out?
> 
> thanks,
> 
> =JeffH
> 

- -- 
ubuntu-users mailing list
[email]ubuntu-users@lists.ubuntu.com[/email]
Modify settings or unsubscribe at: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-users](https://lists.ubuntu.com/mailman/listinfo/ubuntu-users)

---

