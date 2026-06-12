---
title: "Dell Precision 470 &amp; SSD"
date: 2012-08-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Bartender on 2012-08-30
I just wanted to get this out there so nobody wastes a whole day like I did.  As far as I can tell, the [Dell 470 BIOS]("http://support.dell.com/support/edocs/systems/ws470/en/ug_en/advfeat.htm#wp1101281") only gives you an option of RAID ON or RAID OFF.  I cannot find a switch to turn on AHCI.

I wasted several hours (and a good chunk of my satellite internet "allowance") installing/updating 12.04 to an SSD in a Precision 470, only to find that I couldn't get TRIM working.  Followed various [online guides]("http://www.bitsbythepound.com/using-a-solid-state-drive-ssd-with-ubuntu-11-04-409.html").  I went thru the steps, then did the test.  The test failed.  Wasn't sure I followed the directions correctly, so tried again.  Still no joy.

After giving up with the 470, I took the SSD out and stuck it in a PC that I knew was AHCI-capable.  Without making any changes to /etc/fstab, I went thru the test to see if TRIM was working.  Success.

The Precision 470 was built in 2004.  The other PC, the one with AHCI, was built in 2005.  Who knows when Dell introduced AHCI to these workstations.  

It doesn't make a whole lot of sense to install a 6 GB/s SATA III SSD onto a first-generation SATA motherboard.  But just in case others are experimenting, as I was, at least make sure to go into BIOS and check for AHCI capability.

---

