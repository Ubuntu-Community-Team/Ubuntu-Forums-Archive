---
title: "Realtek RTL8139 very slow"
date: 2006-05-03
forum: Desktop Environments
---

### Post by Martin Pilka on 2006-05-03
Hello all,

after the installation of Ubuntu 5.10 on my Acer Aspire 5024 WLMi notebook, my RTL8139 network card operates very slow. ethtool says it is in 100 MBit full duplex mode, network LEDs on both sides also say so. I tested direct cable connection (no switch or hub between) with other computer, providing Samba share, and measuring network speed via jnettop and "date ; cp /mnt/remote_machine/big_file . ; date" method. Here are the results:

<Windows XP> -- <Samba>   9.6 MB/s
<Ubuntu with r8139 driver, noapic> -- <Samba> 1.4 MB/s
<Ubuntu with r8169 driver, apic enabled> -- <Samba> 2.6 MB/s
<Ubuntu with r1000 1.02 driver, noapic> --  <Samba>  4.5 MB/s
<Ubuntu with r1000 1.02 driver, apic enabled> -- <Samba> 2.6 MB/s

If I use noapic, here is my /proc/interrupts:
           CPU0
...
 11:    5006650          XT-PIC  ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3, ATI IXP, yenta, ohci1394, eth0
...
Quite some devices on INT11.

Question is: Why Windows XP is able to do 9.6 MB/s while best I can get from Ubuntu (on the same HW) is 4.5 MB/s (with noapic and r1000 driver downloaded from [www.realtek.com.tw)?](www.realtek.com.tw)?)

Thanks,
Martin

---

### Post by dcstar on 2006-05-04
> **Martin Pilka]Hello all,

after the installation of Ubuntu 5.10 on my Acer Aspire 5024 WLMi notebook, my RTL8139 network card operates very slow. ethtool says it is in 100 MBit full duplex mode, network LEDs on both sides also say so. I tested direct cable connection (no switch or hub between) with other computer, providing Samba share, and measuring network speed via jnettop and "date  said:**
> www.realtek.com.tw)?[/url]
......
Firstly, do a forum search for "disable IPv6", that can cause some network performance issues.

There are also thread around for improving Samba performance by changing the file access type to CIFS (I think), you may also want to search for these.

---

### Post by Martin Pilka on 2006-05-04
Thanks for the tip!

Meanwhile I did some more tests:

<Ubuntu with r1000 1.02 driver, noapic> --SCP-- <Samba> 8.7 MB/s

I use <Samba> just for compatibility with my previous email, actually Samba is not involved in this test at all, it is just the Knoppix machine.

Well, however strange it may sound, it seems that Samba Client in Ubuntu 5.10 is a performance bottle neck. Windows XP can do much better. Do you think it could be the case?

Thanks,
Martin

---

### Post by Martin Pilka on 2006-05-08
Hello again,

some more tests:

smbclient -U guest //192.168.1.2/all_ifne '' -c 'cd install/iso ; get ubuntu-5.10-live-i386.iso'
getting file \install\iso\ubuntu-5.10-live-i386.iso of size 106659840 as ubuntu-5.10-live-i386.iso (8687.2 kb/s) (average 8687.2 kb/s)

/etc/fstab:
//192.168.1.2/sarge /mnt/tmp smbfs password=,gid=users,fmask=664,dmask=775,iocharset=iso8859-2,codepage=cp852,quiet 0 0
mount /mnt/tmp
cp /mnt/tmp/install/iso/ubuntu-5.10-live-i386.iso .
(avg 3 MB/s)

smbfs gives much worse performance than smbclient. I think smbfs is some piece of unmaintained code in Kernel and has nothing to do with Samba.

Now only if I knew how to do "real mount" with smbclient, because it is just FTP-like 
command line tool, can not mount anything.

Martin

---

### Post by Martin Pilka on 2006-05-14
Hello again,

I found out that if you mount using CIFS filesystem (instead of SMBFS), performance is much better, even still does not reach SCP or NFS. I learned that CIFS is a successor of SMBFS.

Meanwhile, I also compared to NFS. How is it possible that with NFS, I can get around 11 MB/s, while with CIFS I can do only 7 MB/s?

Martin

---

