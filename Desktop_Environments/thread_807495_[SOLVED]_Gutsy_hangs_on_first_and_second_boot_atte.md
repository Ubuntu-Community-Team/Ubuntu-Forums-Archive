---
title: "[SOLVED] Gutsy hangs on first and second boot attempt but loads on the third"
date: 2008-05-25
forum: Desktop Environments
---

### Post by JoseArmandoJeronymo on 2008-05-25
This is a pattern in my PC for some weeks now.

At boot-up early in the morning Gutsy collapses just when the clock appears as GDM seems to be loading. The computer stops, the monitor is turned-off. I have to push the reset button. The same thing usually happens a second time. By the third time it has always (so far, touch wood) finished loading and the gnome session started without problems. No anomalies noticed during the day long session.

I have removed and cleaned memory (and some other boards) contacts.

For the sake of testing I have also booted the (legacy) windows partition with no problems.

The crash seems to happen always around the 75th second of the boot up. Here is some extracts from the kernel log:

A. When hanging:

```
May 25 07:13:00 localhost kernel: [   64.841697] PPP generic driver version 2.4.2
May 25 07:13:00 localhost kernel: [   64.881341] NET: Registered protocol family 17
May 25 07:13:00 localhost kernel: [   71.262705] No dock devices found.
May 25 07:13:00 localhost kernel: [   71.359864] input: Power Button (FF) as /class/input/input5
May 25 07:13:00 localhost kernel: [   71.365460] ACPI: Power Button (FF) [PWRF]
May 25 07:13:00 localhost kernel: [   71.401269] input: Power Button (CM) as /class/input/input6
May 25 07:13:00 localhost kernel: [   71.406799] ACPI: Power Button (CM) [PWRB]
May 25 07:13:00 localhost kernel: [   71.444807] input: Sleep Button (CM) as /class/input/input7
May 25 07:13:00 localhost kernel: [   71.450378] ACPI: Sleep Button (CM) [SLPB]
May 25 07:13:01 localhost kernel: [   73.124065] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 16
May 25 07:13:01 localhost kernel: [   73.124088] PCI: Setting latency timer of device 0000:00:1f.6 to 64
May 25 07:13:03 localhost kernel: [   75.155679] [drm] Initialized drm 1.1.0 20060810
May 25 07:13:03 localhost kernel: [   75.161719] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
May 25 07:13:03 localhost kernel: [   75.165167] [drm] Initialized i915 1.6.0 20060119 on minor 0
May 25 07:13:03 localhost kernel: [   75.960614] ppdev: user-space parallel port driver
May 25 07:13:05 localhost kernel: [   77.029123] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May 25 07:13:05 localhost kernel: [   77.029130] apm: overridden by ACPI.
May 25 07:15:21 localhost kernel: Inspecting /boot/System.map-2.6.22-14-386
May 25 07:15:21 localhost kernel: Loaded 24903 symbols from /boot/System.map-2.6.22-14-386.
May 25 07:15:21 localhost kernel: Symbols match kernel version 2.6.22.
May 25 07:15:21 localhost kernel: No module symbols loaded - kernel modules not enabled. 
```

B. When (finally) loading gnome:

```
May 25 07:16:59 localhost kernel: [   61.421586] PPP generic driver version 2.4.2
May 25 07:16:59 localhost kernel: [   61.461283] NET: Registered protocol family 17
May 25 07:16:59 localhost kernel: [   67.690724] No dock devices found.
May 25 07:16:59 localhost kernel: [   67.784137] input: Power Button (FF) as /class/input/input5
May 25 07:16:59 localhost kernel: [   67.789730] ACPI: Power Button (FF) [PWRF]
May 25 07:16:59 localhost kernel: [   67.825635] input: Power Button (CM) as /class/input/input6
May 25 07:16:59 localhost kernel: [   67.831227] ACPI: Power Button (CM) [PWRB]
May 25 07:16:59 localhost kernel: [   67.867105] input: Sleep Button (CM) as /class/input/input7
May 25 07:16:59 localhost kernel: [   67.872564] ACPI: Sleep Button (CM) [SLPB]
May 25 07:17:00 localhost kernel: [   69.351185] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 16
May 25 07:17:00 localhost kernel: [   69.351209] PCI: Setting latency timer of device 0000:00:1f.6 to 64
May 25 07:17:02 localhost kernel: [   71.245536] [drm] Initialized drm 1.1.0 20060810
May 25 07:17:02 localhost kernel: [   71.251712] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
May 25 07:17:02 localhost kernel: [   71.255169] [drm] Initialized i915 1.6.0 20060119 on minor 0
May 25 07:17:03 localhost kernel: [   72.125856] ppdev: user-space parallel port driver
May 25 07:17:03 localhost kernel: [   72.870125] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May 25 07:17:03 localhost kernel: [   72.870132] apm: overridden by ACPI.
May 25 07:18:05 localhost kernel: [  134.709996] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
May 25 07:18:06 localhost kernel: [  135.702828] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
May 25 07:18:06 localhost kernel: [  135.703231] NFSD: starting 90-second grace period
```

I am intrigued by the long time between apm overide by acpi and the knfsd installation.

I have googled and ubuntuforumed the subject and saw some reports of similar but not quite the same problems with kernel 2.6.x.

I am using kernel version 2.6.22-14-386 running on an Intel Celeron 2.66GHz with 496.1MBytes RAM.

I have not tried other kernel versions but booting in the recovery mode for 2.6.22-14 seems to solve the problem.

Thanks for any inputs on the (so far) nuisance.

---

### Post by JoseArmandoJeronymo on 2008-05-27
Looks like the kernel patch distributed yesterday solved the problem.

---

### Post by JoseArmandoJeronymo on 2008-06-14
It didn't! After a few days the problem came back.

---

### Post by JoseArmandoJeronymo on 2008-06-21
Kernel 2.6.22.15-386 since yesterday but the problem remains.

I compared the kern.log lines for today's first (and unsuccessful) attempt with those for the third  (and successful) one. I was hoping to pinpoint the moment where the trains of events would become different but it seems that many instructions did not take place in the same order although nothing that was in the successful boot was missing from the unsuccessful one until the latter collapsed.

I found a funny thing though: in the first and second boot attempts the modem I have in eth1 was identified as eth0 and vice-versa. In the successful boot the id's were correct. However, I reviewed a log from Jun 9 which I had saved and there the modems were correctly id'd in the unsuccessful boot. Extracts of kern.log follow:

```
Boot failed:
Jun  9 19:30:41 localhost kernel: [   27.621866] eth0: VIA Rhine III at 0x1c000, 00:08:54:15:97:d4, IRQ 19. 
Jun  9 19:30:41 localhost kernel: [   27.622590] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1. 
Jun  9 19:30:41 localhost kernel: [   27.622734] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 21 (level, low) -> IRQ 21 
Jun  9 19:30:41 localhost kernel: [   27.623291] eth1: RealTek RTL8139 at 0xe0066000, 00:11:5b:c0:0a:bd, IRQ 21 
Jun  9 19:30:41 localhost kernel: [   27.623295] eth1:  Identified 8139 chip type 'RTL-8100B/8139D' 

Boot successful:
Jun  9 19:34:21 localhost kernel: [   19.419046] eth0: RealTek RTL8139 at 0xe0016000, 00:11:5b:c0:0a:bd, IRQ 21 
Jun  9 19:34:21 localhost kernel: [   19.419049] eth0:  Identified 8139 chip type 'RTL-8100B/8139D' 
Jun  9 19:34:21 localhost kernel: [   19.421586] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004) 
Jun  9 19:34:21 localhost kernel: [   19.424340] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 18 (level, low) -> IRQ 19 
Jun  9 19:34:21 localhost kernel: [   19.429690] eth1: VIA Rhine III at 0x1c000, 00:08:54:15:97:d4, IRQ 19. 
Jun  9 19:34:21 localhost kernel: [   19.430411] eth1: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1. 

Boot successful:
Jun 20 09:18:53 localhost kernel: [   26.415535] eth0: VIA Rhine III at 0x1c000, 00:08:54:15:97:d4, IRQ 19.
Jun 20 09:18:53 localhost kernel: [   26.416258] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
Jun 20 09:18:53 localhost kernel: [   26.418113] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun 20 09:18:53 localhost kernel: [   26.418478] eth1: RealTek RTL8139 at 0xe0016000, 00:11:5b:c0:0a:bd, IRQ 21
Jun 20 09:18:53 localhost kernel: [   26.418481] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'

Boot failed:
Jun 21 10:51:02 localhost kernel: [   26.432741] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun 21 10:51:02 localhost kernel: [   26.433320] eth0: RealTek RTL8139 at 0xe0016000, 00:11:5b:c0:0a:bd, IRQ 21 ***12
Jun 21 10:51:02 localhost kernel: [   26.433324] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Jun 21 10:51:02 localhost kernel: [   26.436416] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jun 21 10:51:02 localhost kernel: [   26.437068] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 18 (level, low) -> IRQ 19
Jun 21 10:51:02 localhost kernel: [   26.442679] eth1: VIA Rhine III at 0x1c000, 00:08:54:15:97:d4, IRQ 19.
Jun 21 10:51:02 localhost kernel: [   26.443404] eth1: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.

Boot failed:
Jun 21 10:58:51 localhost kernel: [   27.005572] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun 21 10:58:51 localhost kernel: [   27.005921] eth0: RealTek RTL8139 at 0xe0016000, 00:11:5b:c0:0a:bd, IRQ 21
Jun 21 10:58:51 localhost kernel: [   27.005924] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Jun 21 10:58:51 localhost kernel: [   27.008548] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jun 21 10:58:51 localhost kernel: [   27.011274] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 18 (level, low) -> IRQ 19
Jun 21 10:58:51 localhost kernel: [   27.016629] eth1: VIA Rhine III at 0x1c000, 00:08:54:15:97:d4, IRQ 19.
Jun 21 10:58:51 localhost kernel: [   27.017350] eth1: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.

Boot successful:
Jun 21 11:01:25 localhost kernel: [   26.460331] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 18 (level, low) -> IRQ 19
Jun 21 11:01:25 localhost kernel: [   26.465663] eth0: VIA Rhine III at 0x1c000, 00:08:54:15:97:d4, IRQ 19.
Jun 21 11:01:25 localhost kernel: [   26.466384] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
Jun 21 11:01:25 localhost kernel: [   26.468213] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun 21 11:01:25 localhost kernel: [   26.468583] eth1: RealTek RTL8139 at 0xe0016000, 00:11:5b:c0:0a:bd, IRQ 21
Jun 21 11:01:25 localhost kernel: [   26.468586] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
```

The only constancy in all kernel logs I have reviewed is that the first operation after the point the system always seems to halt is the loading of knfsd, and that can take a long time to happen. This extracts from today's successful boot agrees with the one previously posted:

```

Jun 21 11:01:28 localhost kernel: [   79.561158] ppdev: user-space parallel port driver
Jun 21 11:01:31 localhost kernel: [   82.330802] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jun 21 11:01:31 localhost kernel: [   82.330809] apm: overridden by ACPI.
Jun 21 11:01:40 localhost kernel: [   90.808297] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Jun 21 11:01:40 localhost kernel: [   90.954356] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jun 21 11:01:40 localhost kernel: [   90.954772] NFSD: starting 90-second grace period
Jun 21 11:01:41 localhost kernel: [   92.212422] Inbound IN=eth1 OUT= MAC=00:11:5b:c0:0a:bd:00:1c:f0:05:dc:bd:08:00 SRC=201.42.154.178 DST=201.42.139.161 LEN=48 TOS=0x00 PREC=0x00 TTL=126 ID=40357 DF PROTO=TCP SPT=4580 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0 
Jun 21 11:01:44 localhost kernel: [   95.177041] Inbound IN=eth1 OUT= MAC=00:11:5b:c0:0a:bd:00:1c:f0:05:dc:bd:08:00 SRC=201.42.154.178 DST=201.42.139.161 LEN=48 TOS=0x00 PREC=0x00 TTL=126 ID=41117 DF PROTO=TCP SPT=4580 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0 
Jun 21 11:02:18 localhost kernel: [  129.041839] Inbound IN=eth1 OUT= MAC=00:11:5b:c0:0a:bd:00:1c:f0:05:dc:bd:08:00 SRC=65.120.238.5 DST=201.42.139.161 LEN=1500 TOS=0x00 PREC=0x00 TTL=52 ID=62833 PROTO=TCP SPT=80 DPT=43058 WINDOW=58400 RES=0x00 ACK URGP=0 

```

Ideas are still welcome :-)

---

### Post by JoseArmandoJeronymo on 2008-06-22
From what I read in [http://tldp.org/HOWTO/ACPI-HOWTO/daemons.html]("http://tldp.org/HOWTO/ACPI-HOWTO/daemons.html") I uninstalled apmd.

The references to apm

```
May 25 07:17:03 localhost kernel: [   72.870125] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May 25 07:17:03 localhost kernel: [   72.870132] apm: overridden by ACPI.
```

present in the previous logs are now gone however the hanging problem remains.

---

### Post by JoseArmandoJeronymo on 2008-06-23
I normally turn both the ADSL modem and the switch off together with the pc so I decided to keep them on for the night wondering if the problem couldn't be the pc not being able to read something from those peripherals for them being running self-tests or something.

No good. PC died at first boot attempt.

---

### Post by JoseArmandoJeronymo on 2008-06-27
I removed nfs-kernel-server and installed nfs-user-server instead.

It has been four days now without the problem. I am now reverting to kernel-server to see if it comes back.

---

### Post by JoseArmandoJeronymo on 2008-06-29
It did come back indeed. Worse, when I switched to nfs-user-server again, the problem was still there when I booted early this morning. It did boot all right on the second attempt.

Kernel log shows this as the last entry before rebooting:

```
Jun 29 09:07:24 localhost kernel: [   77.105460] ppdev: user-space parallel port driver
```

---

### Post by JoseArmandoJeronymo on 2008-06-30
Because I use Canon BJ-200e which is quite old for a printer I wondered if the OS was trying to talk to the printer which being off could not respond thus causing a system stall for some other (unknown reasons).

Well, I decided to turn the printer on before booting to no avail. On the first attempt as gnome tries to load the pc dies. After hitting reset it loaded successfully though.

I noticed another thing: the last instruction logged in auth.log before the stall is 

```
Jun 30 07:44:17 localhost su[7515]: pam_unix(su:session): session closed for user clamav
```

and the first one after that whenever gnome is successful is

```
Jun 30 07:50:30 localhost perl: pam_unix(webmin:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=root
Jun 30 07:50:32 localhost webmin[8822]: Webmin starting

```

I am now purging Webmin (which I don't use anyway) and seeing what happens.

---

### Post by JoseArmandoJeronymo on 2008-07-01
Nothing happened! Still no GDM at first boot attempt.

Well, it just occurred to me that my system is set to automatic defered login. I am changing it to automatic no defering login and (tomorrow morning as usual) seeing what happens.

---

### Post by JoseArmandoJeronymo on 2008-07-06
Playing with login screens I ended up seeing this entry in deamon.log:

```
Jul  2 07:13:14 localhost gdm[7274]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 dceamon.log
```

I googled it and eventually found these two threads:

[http://ubuntuforums.org/showthread.php?t=96068&page=4](http://ubuntuforums.org/showthread.php?t=96068&page=4)
[http://ubuntuforums.org/archive/index.php/t-217741.html](http://ubuntuforums.org/archive/index.php/t-217741.html)

Well, putting it all together I suspected that I have a RAM problem after all and the X server tries to load the login screen and crashes when not finding enough memory while the memory bank is warming up. This explains why the third try was always successful.

The fact is that I substituted the simple login with faces for the ubuntu one with flower, etc and the problem was gone. It has been almost a week I boot without problems.

I am marking this thread solved only hoping that Mr Murphy is not reading these lines and tomorrow my pc boots ok again.:lolflag:

---

### Post by JoseArmandoJeronymo on 2008-07-31
Well, it was all right for a while but when I decided to uninstall some applications the problem came back.

I noticed that the whole boot process took a bit less than usual and then began to believe that I have a memory problem after all: the computer may have to warm up a little before the memory bank is fully operational. I simply changed the time that Grub waits for operator input before loading the default OS from 10 seconds to 4 minutes.

Never had a gnome boot failure again.

So far...

---

