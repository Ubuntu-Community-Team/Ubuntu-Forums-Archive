---
title: "How do i upgrade my BIOS"
date: 2009-06-14
forum: General Help
---

### Post by coolethan on 2009-06-14
how do i upgrade my motherboards BIOS. Here's my setup.

```
ethan@ubuntu:~$ sudo dmidecode | more
[sudo] password for ethan: 
# dmidecode 2.9
SMBIOS 2.3 present.
48 structures occupying 1397 bytes.
Table at 0x000F2B10.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Award Software, Inc.
	Version: ASUS CUV4X-EA ACPI BIOS Revision 1006 Beta 005
	Release Date: 09/05/2002
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 256 kB
	Characteristics:
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
--More--

```

Pentium III processor if that makes a differance

---

### Post by ibuclaw on 2009-06-14
If your motherboard manufacturer has provided one. It will most likely be in a Windows .exe format, so you'll require a windows operating system to carry out the job.


Although, considering the age of your processor, you may be in luck, and the manufacturer may have provided a bootable floppy image too. If that is the case, you dd the .img onto the floppy disk and reboot.

Regards
Iain

---

### Post by coolethan on 2009-06-14
i have windoze xp so that is not a problem. there is a problem however because when looking on the ASUS web page the only model close to mine is the CUV4X-E but sudo dmidecode | more says my board is a CUV4X-EA is that a problem or should the one on the site work with my board.


Edit: nevermind they are the same. it turns out i can't get a newer version of the bios so i'm kind of S.O.L

---

