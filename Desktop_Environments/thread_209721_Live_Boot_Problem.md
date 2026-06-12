---
title: "Live Boot Problem"
date: 2006-07-05
forum: Desktop Environments
---

### Post by baillie on 2006-07-05
Hi,

I have been trying to boot Ubuntu 6.06, but failing, never getting past "mounting root file system", as a lot of people seem to do.

What is weird though is that Knoppix 5.01 and Mandriva One 2006 will both boot with no problems, although SuSE 10.1 won't boot either.

Laptop Specs:
```
Toshiba Equium M50-216 

1.73 gigahertz Intel Pentium M 
TOSHIBA MK4026GAX 40Gb HDD 
TEAC DV-W28E (DVD-RW) 
TOSHIBA ECU00 Motherboard 
512Mb DDR PC2700 RAM 
Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family 
Realtek AC97 Audio 

Other: 
Intel(R) 82801FBM Ultra ATA Storage Controllers 
Texas Instruments PCIxx21/x515 Cardbus Controller 
Intel(R) 82801FB/FBM USB Universal Host Controller 
TOSHIBA Software Modem 
1394 Net Adapter #2 
Intel(R) PRO/Wireless 2200BG Network Connection 
Marvell Yukon 88E8036 PCI-E Fast Ethernet Controller
```

So on the advice of another forum, I tried passing noacpi, with no change, and also removed all USB devices, still no change.

I then booted in verbose mode, to see what errors where being thrown.

Didn't catch all of this one but it was similar to this: ```
ide0: I/O resource 0x1F0-0x1F7 not free.
[4294705.597000] ide0: ports already in use, skipping probe
[4294705.597000] ide1: I/O resource 0x170-0x177 not free.
[4294705.597000] ide1: ports already in use, skipping probe
```

It then repeated this, every few seconds or so: ```
buffer i/o error on device sr0 logical block 357296
```

My hunch is that my DVDRW is involved in this, and is causing the problem, how I haven't a clue, but thats why I'm here!

The disc i am using has been md5 checked after downloading, and burnt using Nero at the slowest speed possible.

After a lot of looking around, and googling I found this: [http://kerneltrap.org/node/3971](http://kerneltrap.org/node/3971), this appears to be very similar to what I am experiencing.

Am I 1 or 2 boot options away from success or am I heading into a world of trouble trying to get Ubuntu installed on this machine?

Thanks

---

### Post by wjcook on 2006-07-05
I have the exact same problem with the identical result, "buffer i/o...".

I tried the CDROM on another computer and I thought it stalled again at the "Mounting root file system" but it finally booted.  I had no other problems with this computer.

I tried once again on the other computer and received the same results.  Knoppix works fine with no problem.  The device drivers for the CDROM must not be compatable with my Sony DVD/RW drive or the system does not know how to mount or read the drive.  Although it does get to a certain point before it fails.

---

