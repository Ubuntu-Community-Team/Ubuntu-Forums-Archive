---
title: "Can't get into the GUI - read-only file system errors"
date: 2019-03-19
forum: Desktop Environments
---

### Post by peyre on 2019-03-19
Last night I hooked up an old parallel zip drive to my desktop (I want to read some old disks) running Xubuntu 18.10 64-bit.  I edited /etc/modules to add **imm** and rebooted.  It booted up fine and I could read disks, but now my system won't load the GUI.  It boots to the command line and I sign on, then it shows the following:
```
/usr/lib/ubuntu-release-upgrader/release-upgrade-motd: 31: /usr/lib/ubuntu-release-upgrader/release-upgrade-motd: cannot create /var/lib/ubuntu-release-upgrader/release-upgrade-available: Read-only file system
mktemp: failed to create file via template '/var/lib/update-notifier/tmp.XXXXXXXXXX': Read-only file system
run-parts: /etc/update-motd.d/95-hwe-eol exited with return code 1
/usr/lib/update-notifier/update-motd-fsck-at-reboot: 33: /usr/lib/update-notifier/update-motd-fsck-at-reboot: cannot create /var/lib/update-notifier/fsck-at-reboot: Read-only file system
```

I have removed imm from /etc/modules but it's still doing the same thing.

I've noticed that on bootup it asks what I want to boot; the above is what I get if I select Xubuntu.  I've gone into advanced options and tried recovery mode, let it try to fsck, dpkg, and clean, but those haven't helped.  On continuing bootup it goes to a command line in lower resolution, and displays the same read-only $#@! mentioned above.  What can I do about this?

Also, I've noticed that during bootup, I see a screen full of these two lines repeated over and over:
```
[  OK  ]  Stopped Network Time Synchronization.
[FAILED]  Failed to start Network Time Synchronization.
See 'systemctl status systemd-timesyncd.service' for details.
```

When I run **systemctl status systemd-timesyncd.service** I get the following:
```
&#8226; systemd-timesyncd.service - Network Time Synchronization
  Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; vendor preset: enabled)
  Active: [COLOR="#FF0000"]failed[/COLOR] (Result: resources) since Tue 2019-03-19 19:30:54 PDT; 14min ago
    Docs: man:systemd-timesyncd.service(8)

Mar 19 19:30:54 peyre systemd[1]: Stopped Network Time Synchronization.
Mar 19 19:30:54 peyre systemd[1]: systemd-timesyncd.service: Start request repeated too quickly.
Mar 19 19:30:54 peyre systemd[1]: systemd-timesyncd.service: Failed with result 'resources'.
Mar 19 19:30:54 peyre systemd[1]: Failed to start Network Time Synchronization.
Mar 19 19:30:54 peyre systemd[1]: systemd-timesyncd.service: Start request repeated too quickly.
Mar 19 19:30:54 peyre systemd[1]: systemd-timesyncd.service: Failed with result 'resources'.
Mar 19 19:30:54 peyre systemd[1]: Failed to start Network Time Synchronization.Mar 19 19:30:54 peyre systemd[1]: systemd-timesyncd.service: Start request repeated too quickly.
Mar 19 19:30:54 peyre systemd[1]: systemd-timesyncd.service: Failed with result 'resources'.
Mar 19 19:30:54 peyre systemd[1]: Failed to start Network Time Synchronization.
```

---

### Post by TheFu on 2019-03-20
I would make a great backup of everything I didn't want to loose. That's the first thing, before anything else.  Job #1.

I would guess this is an unfortunate coincidence.  Something about the storage subsystem is failing.
I'd check **dmesg** for errors and run SMART tests on the storage.  If the storage is an SSD, this is about the nicest way I've seen it hint that failure is going to happen any time now.

The time-sync stuff could just be due to the read-only disk - no place to create temporary files necessary to running any Ubuntu.

I'd get a live-boot flash drive ready if you don't have one already.  Does the live-boot work perfectly?  That would help to remove the on-board storage from the equation, since it won't be used.  If there are failures with the live-boot even when the other storage isn't being used, then something else is wrong.

---

### Post by peyre on 2019-03-20
Oh no!  I hope it's not the system drive.  That's only a few months old, and yes it's an SSD.  I know they can fail at any time and sometimes do fairly early.  I also think you're right that the zip drive thing is a coincidence, since undoing the change didn't make a difference.

Fortunately I back up my data fairly often; most of it's on the second (mechanical) drive on the machine anyway and shouldn't be affected.  But the computer does boot successfully with an 18.10 Xubuntu DVD.  I fired it up this morning to try to back up my home directory before heading to work, but the SOB insisted on mounting my external HD as read-only.  When I finally got it to mount a flash drive RW, it kept complaining about not having permission to copy my .wine folder, then my Desktop folder.  Finally I just shut it down and put it off til tonight so I could catch my train this morning.

Tonight I'll find a way to back up my home directory (the important parts anyway), and I'll boot with an old Lubuntu CD, which has a Disk Utility installed, so I can check the SMART data.  I'll be pretty disappointed if this nice new SSD fails and I have to get a new one and reinstall my main system all over from scratch, but if that's the way it turns out to be, I'll manage.

---

### Post by TheFu on 2019-03-20
If your backups take longer than 45 min to restore with the same data and same programs re-installed, I think you are doing backups wrong.  No need to clone a disk or make a 100% mirror. I don't backup the core OS at all, just the settings, data, and list of installed packages.  Just being smart about the stuff you actually do backup, so it is easy to put back.  **apt-mark** is a fantastic tool, just sayin'.

Obviously, if you have multiple TB of data, restore will take longer, but for the core 25G that makes an OS and OS customized for you, 30-45m is all a restore should take.

---

### Post by peyre on 2019-03-20
The problem wasn't that data transfer was taking too long and I wasn't doing a restore.  I was trying to copy the important subfolders in my home directory (Desktop, Downloads, Pictures, etc.) and it wasn't allowing me to do it at all.

---

### Post by TheFu on 2019-03-20
Daily, automatic, versioned, backups.  Accept no substitutes.  My backups take ... let me check ... last night they took:
```
ElapsedTime 11.30 (11.30 seconds)
ElapsedTime 285.49 (4 minutes 45.49 seconds)   # My main desktop 
ElapsedTime 19.52 (19.52 seconds)                # fairly new "server"
ElapsedTime 182.73 (3 minutes 2.73 seconds)
ElapsedTime 47.11 (47.11 seconds)
ElapsedTime 263.97 (4 minutes 23.97 seconds)
ElapsedTime 124.64 (2 minutes 4.64 seconds)   # Nextcloud server
ElapsedTime 484.00 (8 minutes 4.00 seconds)   # main laptop
ElapsedTime 1666.67 (27 minutes 46.67 seconds)  # email server w/ many hundreds of thousands of tiny files.

```

Don't forget to see if re-seating the connections for the SSD don't fix the issue, but if 1 directory is having permissions issues -** ls -l** shows ?????????? in the permissions area, there is corruption.  Going into read-only mode is the storage device trying to prevent even more damage. At some point, all access will end. Then it is time to drill some holes through the storage and trash it.

I've had 2 SSDs fail in the last 5 yrs.  They were relatively cheap, small, m.2 4422 NF SATA devices.  Last month, I picked up a 2.5" SATA 500G SSD - a Samsung EVO 860. This is a well regarded SSD with a long warranty.  I'm in the market for an m.2 NMVe SSD for a fairly new "server" that will run lots of VMs.

But I will continue to perform daily, automatic, versioned, backups. ;)

---

### Post by peyre on 2019-03-20
Ah!  No, I just have a shell script that copies off everything important to my ext HD.  My data doesn't change so often that I feel a need for daily (or even weekly) backups.

I hadn't thought about reseating the connections to the SSD!  Must try that first tonight.  That and the **ls -l** tip you mention sound like first-rate troubleshooting ideas.

---

### Post by TheFu on 2019-03-20
> **peyre said:**
> Ah!  No, I just have a shell script that copies off everything important to my ext HD.  My data doesn't change so often that I feel a need for daily (or even weekly) backups.

I hadn't thought about reseating the connections to the SSD!  Must try that first tonight.  That and the **ls -l** tip you mention sound like first-rate troubleshooting ideas.

The SMART data is probably the most useful advice.  It will say if the disk or cable is the issue. Re-seating likely won't change anything, but once in 20 times, it does.

We all start out doing the "I'll copy it as a backup" until we are burned.  Next is the weekly, automatic, rsync ... until we are burned.  Then most people get to the "I need a real backup" and try to figure it out.   At least this is what happened to me. I think it is fairly common.
 
BTW, my backups are not just efficient in the copy, but also in the storage.  i keep 60-180 days of versioned backups for each system and it all fits onto 1 USB2 external HDD.  Media is backed up differently, so that is just the normal OS stuff and HOME directory data. You know, the things that do change all the time, but are fairly small.

---

### Post by peyre on 2019-03-20
Hm!  Ok, maybe my game plan will be: 
1) Open computer and reseat the SSD, close it back up
2) Try booting normally
3) Boot from Lubuntu disk and check SMART data, and see where we are at that point

I've been using this .sh script for probably a decade.  I use the same ext HD to back up my wife's computer with a batch file, then every few months I bring it in to the office and swap it out with our other ext HD, to keep an offsite copy of our data.

---

### Post by peyre on 2019-03-20
Well, reseating didn't help.  Was worth a try though!

Disk Utility shows the disk is healthy, and all the attributes look good after an Extended test.  Of course, SMART data is famous for false negatives.  I'll back up my data at this point; maybe someone can suggest something to try next?

---

### Post by peyre on 2019-03-21
Bump?  Anyone?  If not, I'll probably wipe the drive tonight.  Stop me if you think there's a better plan.

---

### Post by TheFu on 2019-03-21
How to say this ... still waiting for any data.  Cannot help without some facts.

Claiming that data says something is very different than showing the data. I never saw anything about dmesg or logs or SMART data or even the ls -l output.

If you boot from older Releases like 18.04 or 16.04, does the drive open read-write? Sometimes newer kernels have odd issues.  After all, 18.10 is really new and non-LTS releases shouldn't be used in production.  New is the enemy of stable.

---

### Post by peyre on 2019-03-21
Ah, right.  I'll try that.  Might be tricky mounting a flash drive so I can copy & paste the results here, but I'll do what I can.

---

### Post by peyre on 2019-03-21
I must admit I'm a noob at doing command-line mounts, but I can't seem to mount the damn thing  because it insists that, say, /media/leon is a read-only file system, so it won't let me create a subfolder there.

--Aha!  I was able to save onto the other hard drive...should've thought of that sooner.  Here is the result of **ls -l**:
```

total 12252
-rw-r--r--  1 leon leon   50078 Dec 27 16:36 AT&T Dial-Up Numbers.txt
drwxrwxr-x  3 leon leon    4096 Mar  5 09:40 Calibre Library
-rw-r--r--  1 leon leon      99 Aug 24  2016 Cell Phone numbers.txt
-rw-rw-r--  1 leon leon    2032 Jan 17 20:32 Compiling RIS.txt
-rwxrwxr-x  1 leon leon     921 May 20  2016 copy_c_drive_data.bat
drwxr-xr-x  5 leon leon    4096 Mar 11 20:04 Desktop
drwxr-xr-x  4 leon leon    4096 Feb 27  2018 Documents
drwxrwxr-x 62 leon leon    4096 Jan  9 19:54 dos
-rwxrwxr-x  1 leon leon     225 May 20  2016 Download.htm
drwxr-xr-x 31 leon leon   12288 Mar 18 21:39 Downloads
drwxr-xr-x  2 leon leon   12288 Feb 24 19:59 dwhelper
-rw-rw-r--  1 leon leon  539032 Oct 21 10:43 FirstMenInMoon1919.png
-rwxrwxr-x  1 leon leon     665 May 20  2016 First Men in the Moon.rip
-rw-rw-r--  1 leon leon   40207 Feb 15 20:20 Floppy RW mount options.jpg
-rw-rw-r--  1 leon leon  315733 Jan 27 15:42 Frontier.pdf
-rwxrwxr-x  1 leon leon 7365604 May 20  2016 history.dat
drwxrwxr-x  9 leon leon    4096 Jan 20 10:11 Hold
drwxrwxr-x  5 leon leon    4096 May 28  2017 Icons
-rw-rw-r--  1 leon leon 1663940 Jun  5  2016 If I should die before I wake - CalPERS.jpeg
-rwxrwxr-x  1 leon leon   19594 Sep 17  2018 If I should die before I wake.txt
-rwxrwxr-x  1 leon leon   10752 May 20  2016 If I should die before I wake Will addendum.doc
-rwxrwxr-x  1 leon leon      44 May 20  2016 Laura & the Hose.txt
-rwxrwxr-x  1 leon leon    1692 May 20  2016 leonbackup.sh
-rwxrwxr-x  1 leon leon    4489 May 20  2016 leon.kmy
-rw-rw-r--  1 leon leon    4106 Mar 10  2017 Marguerite1.flb
-rw-rw-r--  1 leon leon    4332 Jun 17  2017 Marguerite2.flb
-rw-rw-r--  1 leon leon    4331 Jul  5  2017 Marguerite3.flb
-rw-rw-r--  1 leon leon    4345 Nov  5  2017 Marguerite4.flb
-rw-rw-r--  1 leon leon    4340 Nov 29  2017 Marguerite5.flb
-rw-r--r--  1 leon leon      37 Mar 28  2017 Mike & Kay.txt
-rw-r--r--  1 leon leon      58 Mar 28  2017 Mom's neighbors etc.txt
-rwxrwxr-x  1 leon leon      63 May 20  2016 mountcd
drwxr-x---  2 leon leon    4096 Jan 18  2017 multipageproject
drwxr-xr-x  2 leon leon    4096 Jan  5  2017 Music
-rw-rw-r--  1 leon leon       0 Jan 25  2017 netstat.log
-rw-rw-r--  1 leon leon    4105 Sep  5  2016 Pete1.flb
-rw-rw-r--  1 leon leon    3939 Sep 15  2016 Pete2.flb
-rw-rw-r--  1 leon leon    4114 Oct 19  2016 Pete3.flb
-rw-rw-r--  1 leon leon    4037 Nov 30  2016 Pete4.flb
drwxr-xr-x  4 leon leon    4096 May 18  2018 Pictures
lrwxrwxrwx  1 leon leon      36 Nov 24 13:22 PlayOnLinux's virtual drives -> /home/leon/.PlayOnLinux//wineprefix/
drwxrwxr-x  4 leon leon    4096 Nov 22 09:22 prefix32
drwxr-xr-x  2 leon leon    4096 Jan  5  2017 Public
drwxr-xr-x 10 leon leon    4096 Jan 26 15:24 raceintospace
drwxr-xr-x  8 leon leon    4096 Jan 26 15:27 raceintospace-go
drwx------  8 leon leon    4096 Aug 30  2012 RIS_CVS
-rwxrwxr-x  1 leon leon  819200 May 20  2016 riskboot.dsk
-rwxrwxr-x  1 leon leon   62548 May 20  2016 SBC Dial-up Numbers.txt
drwxr-xr-x  7 leon leon    4096 Dec 20 08:12 snap
-rw-rw-r--  1 leon leon  122963 Jan 27 15:42 Southwest.pdf
-rwxrwxr-x  1 leon leon  217088 May 20  2016 SpaceMonger.exe
-rwxr-xr-x  1 leon leon       0 Jan 18 18:33 Special Characters (Unicode) - Cyrillic.docx
-rwxrwxr-x  1 leon leon     881 Jan 21 18:18 Special Characters (Unicode).txt
drwxrwxr-x  3 leon leon    4096 Apr 26  2017 Steam
drwxrwxrwx 32 leon root   12288 Mar 21 20:08 Storage
-rwxrwxrwx  1 leon leon 1048576 Mar  4 07:15 stuff.tc
drwxr-xr-x  2 leon leon    4096 Aug  7  2018 SuperShuttle-Depart_files
-rw-r--r--  1 leon leon    2128 May 21  2016 sysctl.conf
drwxr-xr-x  2 leon leon    4096 Apr 19  2017 Templates
-rwxrwxr-x  1 leon leon     158 May 21  2016 TrueCrypt.desktop
drwxr-xr-x  2 leon leon    4096 Mar  1  2017 Videos
drwxrwxr-x  2 leon leon    4096 Oct  2 21:55 VirtualBox VMs

```

and **dmesg**:
```

[    0.000000] microcode: microcode updated early to revision 0x60f, date = 2010-09-29
[    0.000000] Linux version 4.18.0-16-generic (buildd@lcy01-amd64-022) (gcc version 8.2.0 (Ubuntu 8.2.0-7ubuntu1)) #17-Ubuntu SMP Fri Feb 8 00:06:57 UTC 2019 (Ubuntu 4.18.0-16.17-generic 4.18.20)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-16-generic root=UUID=e44fc5f7-5e7e-4735-a69c-3df725978085 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: x87 FPU will use FXSAVE
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfedffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfee0000-0x00000000bfee2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bfee3000-0x00000000bfeeffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bfef0000-0x00000000bfefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. G31M-ES2L/G31M-S2L, BIOS F10 09/29/2009
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CCFFF write-protect
[    0.000000]   CD000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.000000] total RAM covered: 4095M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] e820: update [mem 0xbff00000-0xffffffff] usable ==> reserved
[    0.000000] last_pfn = 0xbfee0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f5230-0x000f523f] mapped at [(____ptrval____)]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [(____ptrval____)] 99000 size 24576
[    0.000000] BRK [0x2c760000, 0x2c760fff] PGTABLE
[    0.000000] BRK [0x2c761000, 0x2c761fff] PGTABLE
[    0.000000] BRK [0x2c762000, 0x2c762fff] PGTABLE
[    0.000000] BRK [0x2c763000, 0x2c763fff] PGTABLE
[    0.000000] BRK [0x2c764000, 0x2c764fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x33449000-0x35a1bfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F6C20 000014 (v00 GBT   )
[    0.000000] ACPI: RSDT 0x00000000BFEE3040 000038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 0x00000000BFEE30C0 000074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 0x00000000BFEE3180 0040E8 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS 0x00000000BFEE0000 000040
[    0.000000] ACPI: HPET 0x00000000BFEE73C0 000038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 0x00000000BFEE7440 00003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC 0x00000000BFEE72C0 000084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT 0x00000000BFEE7AE0 0003AB (v01 PmRef  CpuPm    00003000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000013fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x13ffd2000-0x13fffcfff]
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000013fffffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000bfedffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000013fffffff]
[    0.000000] Reserved but unavailable: 386 pages
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000013fffffff]
[    0.000000] On node 0 totalpages: 1048190
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12220 pages used for memmap
[    0.000000]   DMA32 zone: 782048 pages, LIFO batch:31
[    0.000000]   Normal zone: 4096 pages used for memmap
[    0.000000]   Normal zone: 262144 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfee0000-0xbfee2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfee3000-0xbfeeffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfef0000-0xbfefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
[    0.000000] [mem 0xbff00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] random: get_random_bytes called from start_kernel+0x99/0x55a with crng_init=0
[    0.000000] setup_percpu: NR_CPUS:8192 nr_cpumask_bits:4 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] percpu: Embedded 46 pages/cpu @(____ptrval____) s151552 r8192 d28672 u524288
[    0.000000] pcpu-alloc: s151552 r8192 d28672 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists, mobility grouping on.  Total pages: 1031789
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-16-generic root=UUID=e44fc5f7-5e7e-4735-a69c-3df725978085 ro quiet splash
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3993400K/4192760K available (12300K kernel code, 2633K rwdata, 4352K rodata, 2456K init, 2336K bss, 199360K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Kernel/User page tables isolation: enabled
[    0.000000] ftrace: allocating 40831 entries in 160 pages
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=4.
[    0.000000] 	Tasks RCU enabled.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS: 524544, nr_irqs: 456, preallocated irqs: 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] ACPI: Core revision 20180531
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] APIC: Switch to symmetric I/O mode setup
[    0.000000] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.020000] tsc: Fast TSC calibration using PIT
[    0.024000] tsc: Detected 2499.988 MHz processor
[    0.024000] clocksource: tsc-early: mask: 0xffffffffffffffff max_cycles: 0x24092e36be0, max_idle_ns: 440795214094 ns
[    0.024000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4999.97 BogoMIPS (lpj=9999952)
[    0.024000] pid_max: default: 32768 minimum: 301
[    0.024000] Security Framework initialized
[    0.024000] Yama: becoming mindful.
[    0.024000] AppArmor: AppArmor initialized
[    0.029482] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.030579] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.030650] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.030686] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.031027] mce: CPU supports 6 MCE banks
[    0.031037] CPU0: Thermal monitoring enabled (TM2)
[    0.031039] process: using mwait in idle threads
[    0.031044] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.031045] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.031048] Spectre V2 : Mitigation: Full generic retpoline
[    0.031049] Spectre V2 : Spectre v2 / SpectreRSB mitigation: Filling RSB on context switch
[    0.031050] Speculative Store Bypass: Vulnerable
[    0.031188] Freeing SMP alternatives memory: 36K
[    0.036000] smpboot: CPU0: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz (family: 0x6, model: 0x17, stepping: 0x6)
[    0.036000] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.036000] ... version:                2
[    0.036000] ... bit width:              40
[    0.036000] ... generic registers:      2
[    0.036000] ... value mask:             000000ffffffffff
[    0.036000] ... max period:             000000007fffffff
[    0.036000] ... fixed-purpose events:   3
[    0.036000] ... event mask:             0000000700000003
[    0.036000] Hierarchical SRCU implementation.
[    0.036000] NMI watchdog: Enabled. Permanently consumes one hw-PMU counter.
[    0.036000] smp: Bringing up secondary CPUs ...
[    0.036000] x86: Booting SMP configuration:
[    0.036000] .... node  #0, CPUs:      #1
[    0.040038] smp: Brought up 1 node, 2 CPUs
[    0.040038] smpboot: Max logical packages: 2
[    0.040038] smpboot: Total of 2 processors activated (9999.95 BogoMIPS)
[    0.041540] devtmpfs: initialized
[    0.041540] x86/mm: Memory block size: 128MB
[    0.041540] PM: Registering ACPI NVS region [mem 0xbfee0000-0xbfee2fff] (12288 bytes)
[    0.044015] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.044015] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.044090] pinctrl core: initialized pinctrl subsystem
[    0.044224] RTC time:  3:18:50, date: 03/22/19
[    0.044378] NET: Registered protocol family 16
[    0.044493] audit: initializing netlink subsys (disabled)
[    0.044502] audit: type=2000 audit(1553224730.044:1): state=initialized audit_enabled=0 res=1
[    0.044502] cpuidle: using governor ladder
[    0.044502] cpuidle: using governor menu
[    0.044502] ACPI: bus type PCI registered
[    0.044502] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.044502] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.044502] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.044502] PCI: Using configuration type 1 for base access
[    0.045677] HugeTLB registered 2.00 MiB page size, pre-allocated 0 pages
[    0.045677] ACPI: Added _OSI(Module Device)
[    0.045677] ACPI: Added _OSI(Processor Device)
[    0.045677] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.045677] ACPI: Added _OSI(Processor Aggregator Device)
[    0.045677] ACPI: Added _OSI(Linux-Dell-Video)
[    0.045677] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.050759] ACPI: 2 ACPI AML tables successfully acquired and loaded
[    0.053703] ACPI: Dynamic OEM Table Load:
[    0.053711] ACPI: SSDT 0xFFFF8ED47A555400 0002AE (v01 PmRef  Cpu0Ist  00003000 INTL 20040311)
[    0.054058] ACPI: Dynamic OEM Table Load:
[    0.054062] ACPI: SSDT 0xFFFF8ED47A5F7600 000152 (v01 PmRef  Cpu1Ist  00003000 INTL 20040311)
[    0.054482] ACPI: Interpreter enabled
[    0.054505] ACPI: (supports S0 S3 S4 S5)
[    0.054507] ACPI: Using IOAPIC for interrupt routing
[    0.054543] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.054741] ACPI: Enabled 9 GPEs in block 00 to 1F
[    0.061330] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.061337] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.061342] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.061668] PCI host bridge to bus 0000:00
[    0.061671] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.061673] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.061674] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.061676] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
[    0.061678] pci_bus 0000:00: root bus resource [mem 0xbff00000-0xfebfffff window]
[    0.061680] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.061690] pci 0000:00:00.0: [8086:29c0] type 00 class 0x060000
[    0.061826] pci 0000:00:01.0: [8086:29c1] type 01 class 0x060400
[    0.061870] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.061999] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
[    0.062019] pci 0000:00:1b.0: reg 0x10: [mem 0xfdff8000-0xfdffbfff 64bit]
[    0.062085] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.062207] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.062279] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.062400] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
[    0.062471] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.062597] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.062637] pci 0000:00:1d.0: reg 0x20: [io  0xff00-0xff1f]
[    0.062760] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.062800] pci 0000:00:1d.1: reg 0x20: [io  0xfe00-0xfe1f]
[    0.062924] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.062963] pci 0000:00:1d.2: reg 0x20: [io  0xfd00-0xfd1f]
[    0.063088] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.063127] pci 0000:00:1d.3: reg 0x20: [io  0xfc00-0xfc1f]
[    0.063258] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.063277] pci 0000:00:1d.7: reg 0x10: [mem 0xfdfff000-0xfdfff3ff]
[    0.063449] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.063603] pci 0000:00:1f.0: [8086:27b8] type 00 class 0x060100
[    0.063682] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH6 ACPI/GPIO/TCO
[    0.063686] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
[    0.063689] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.063692] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.063818] pci 0000:00:1f.2: [8086:27c0] type 00 class 0x010180
[    0.063833] pci 0000:00:1f.2: reg 0x10: [io  0x0000-0x0007]
[    0.063840] pci 0000:00:1f.2: reg 0x14: [io  0x0000-0x0003]
[    0.063847] pci 0000:00:1f.2: reg 0x18: [io  0x0000-0x0007]
[    0.063854] pci 0000:00:1f.2: reg 0x1c: [io  0x0000-0x0003]
[    0.063861] pci 0000:00:1f.2: reg 0x20: [io  0xf900-0xf90f]
[    0.063875] pci 0000:00:1f.2: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.063877] pci 0000:00:1f.2: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.063879] pci 0000:00:1f.2: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.063880] pci 0000:00:1f.2: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.063901] pci 0000:00:1f.2: PME# supported from D3hot
[    0.064012] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.064064] pci 0000:00:1f.3: reg 0x20: [io  0x0500-0x051f]
[    0.064227] pci 0000:01:00.0: [10de:0622] type 00 class 0x030000
[    0.064243] pci 0000:01:00.0: reg 0x10: [mem 0xfa000000-0xfaffffff]
[    0.064253] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.064262] pci 0000:01:00.0: reg 0x1c: [mem 0xf8000000-0xf9ffffff 64bit]
[    0.064269] pci 0000:01:00.0: reg 0x24: [io  0xaf00-0xaf7f]
[    0.064276] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0007ffff pref]
[    0.064282] pci 0000:01:00.0: enabling Extended Tags
[    0.064384] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.064387] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.064390] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.064393] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.064437] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.064440] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.064444] pci 0000:00:1c.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.064448] pci 0000:00:1c.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.064504] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.064530] pci 0000:03:00.0: reg 0x10: [io  0xbe00-0xbeff]
[    0.064556] pci 0000:03:00.0: reg 0x18: [mem 0xfdeff000-0xfdefffff 64bit pref]
[    0.064573] pci 0000:03:00.0: reg 0x20: [mem 0xfdee0000-0xfdeeffff 64bit pref]
[    0.064584] pci 0000:03:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
[    0.064665] pci 0000:03:00.0: supports D1 D2
[    0.064666] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.064762] pci 0000:00:1c.1: ASPM: current common clock configuration is broken, reconfiguring
[    0.076030] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.076036] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.076042] pci 0000:00:1c.1:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.076049] pci 0000:00:1c.1:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.076075] pci_bus 0000:04: extended config space not accessible
[    0.076154] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.076157] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.076160] pci 0000:00:1e.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.076165] pci 0000:00:1e.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.076167] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.076168] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.076170] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.076172] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff window] (subtractive decode)
[    0.076174] pci 0000:00:1e.0:   bridge window [mem 0xbff00000-0xfebfffff window] (subtractive decode)
[    0.077020] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.077120] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.077219] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.077318] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.077417] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.077516] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.077614] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.077714] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.078175] SCSI subsystem initialized
[    0.078188] libata version 3.00 loaded.
[    0.078188] pci 0000:01:00.0: vgaarb: setting as boot VGA device
[    0.078188] pci 0000:01:00.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.078188] pci 0000:01:00.0: vgaarb: bridge control possible
[    0.078188] vgaarb: loaded
[    0.078188] ACPI: bus type USB registered
[    0.078188] usbcore: registered new interface driver usbfs
[    0.078188] usbcore: registered new interface driver hub
[    0.078188] usbcore: registered new device driver usb
[    0.078188] pps_core: LinuxPPS API ver. 1 registered
[    0.078188] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.078188] PTP clock support registered
[    0.078188] EDAC MC: Ver: 3.0.0
[    0.078188] PCI: Using ACPI for IRQ routing
[    0.084144] PCI: pci_cache_line_size set to 64 bytes
[    0.084184] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.084186] e820: reserve RAM buffer [mem 0xbfee0000-0xbfffffff]
[    0.084317] NetLabel: Initializing
[    0.084318] NetLabel:  domain hash size = 128
[    0.084318] NetLabel:  protocols = UNLABELED CIPSOv4 CALIPSO
[    0.084338] NetLabel:  unlabeled traffic allowed by default
[    0.084603] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.084608] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.084612] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.086637] clocksource: Switched to clocksource tsc-early
[    0.102728] VFS: Disk quotas dquot_6.6.0
[    0.102758] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.102938] AppArmor: AppArmor Filesystem Enabled
[    0.102982] pnp: PnP ACPI init
[    0.103231] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    0.103233] system 00:00: [io  0x0290-0x029f] has been reserved
[    0.103235] system 00:00: [io  0x0800-0x087f] has been reserved
[    0.103237] system 00:00: [io  0x0290-0x0294] has been reserved
[    0.103239] system 00:00: [io  0x0880-0x088f] has been reserved
[    0.103246] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.103352] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.103555] pnp 00:02: [dma 2]
[    0.103596] pnp 00:02: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.103906] pnp 00:03: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.104380] pnp 00:04: [dma 3]
[    0.104432] pnp 00:04: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.104567] system 00:05: [io  0x0400-0x04cf] could not be reserved
[    0.104573] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.104884] system 00:06: [mem 0xe0000000-0xefffffff] has been reserved
[    0.104889] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.105202] system 00:07: [mem 0x000cd400-0x000cffff] has been reserved
[    0.105204] system 00:07: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.105206] system 00:07: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.105208] system 00:07: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.105210] system 00:07: [mem 0xbfee0000-0xbfefffff] could not be reserved
[    0.105212] system 00:07: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.105214] system 00:07: [mem 0x00100000-0xbfedffff] could not be reserved
[    0.105216] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.105219] system 00:07: [mem 0xfed13000-0xfed1dfff] has been reserved
[    0.105221] system 00:07: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.105223] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.105225] system 00:07: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.105227] system 00:07: [mem 0xfff00000-0xffffffff] has been reserved
[    0.105229] system 00:07: [mem 0x000e0000-0x000effff] has been reserved
[    0.105234] system 00:07: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.105241] pnp: PnP ACPI: found 8 devices
[    0.111672] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.111707] pci 0000:01:00.0: BAR 6: assigned [mem 0xfb000000-0xfb07ffff pref]
[    0.111709] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.111712] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.111715] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.111718] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.111721] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.111724] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.111728] pci 0000:00:1c.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.111731] pci 0000:00:1c.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.111737] pci 0000:03:00.0: BAR 6: assigned [mem 0xfd900000-0xfd90ffff pref]
[    0.111739] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.111741] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.111745] pci 0000:00:1c.1:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.111748] pci 0000:00:1c.1:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.111754] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.111756] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.111760] pci 0000:00:1e.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.111763] pci 0000:00:1e.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.111769] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.111771] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.111773] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.111774] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff window]
[    0.111776] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xfebfffff window]
[    0.111778] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.111780] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbffffff]
[    0.111781] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.111783] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.111785] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.111786] pci_bus 0000:02: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.111788] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.111790] pci_bus 0000:03: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.111791] pci_bus 0000:03: resource 2 [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.111793] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.111795] pci_bus 0000:04: resource 1 [mem 0xfdc00000-0xfdcfffff]
[    0.111796] pci_bus 0000:04: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.111798] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7 window]
[    0.111800] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff window]
[    0.111802] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.111803] pci_bus 0000:04: resource 7 [mem 0x000c0000-0x000dffff window]
[    0.111805] pci_bus 0000:04: resource 8 [mem 0xbff00000-0xfebfffff window]
[    0.111906] NET: Registered protocol family 2
[    0.112200] tcp_listen_portaddr_hash hash table entries: 2048 (order: 3, 32768 bytes)
[    0.112229] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.112339] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.112510] TCP: Hash tables configured (established 32768 bind 32768)
[    0.112575] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.112601] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.112666] NET: Registered protocol family 1
[    0.112672] NET: Registered protocol family 44
[    0.113552] pci 0000:01:00.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    0.113558] PCI: CLS 4 bytes, default 64
[    0.113621] Unpacking initramfs...
[    0.757573] Freeing initrd memory: 38732K
[    0.757605] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.757609] software IO TLB [mem 0xbbee0000-0xbfee0000] (64MB) mapped at [(____ptrval____)-(____ptrval____)]
[    0.757794] Scanning for low memory corruption every 60 seconds
[    0.758627] Initialise system trusted keyrings
[    0.758642] Key type blacklist registered
[    0.758718] workingset: timestamp_bits=36 max_order=20 bucket_order=0
[    0.760738] zbud: loaded
[    0.761402] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    0.761670] fuse init (API version 7.27)
[    0.761758] pstore: using deflate compression
[    0.763268] Key type asymmetric registered
[    0.763270] Asymmetric key parser 'x509' registered
[    0.763330] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 244)
[    0.763366] io scheduler noop registered
[    0.763367] io scheduler deadline registered
[    0.763405] io scheduler cfq registered (default)
[    0.763990] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    0.764069] intel_idle: does not run on family 6 model 23
[    0.764176] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.764187] ACPI: Power Button [PWRB]
[    0.764246] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.764262] ACPI: Power Button [PWRF]
[    0.764623] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.785048] 00:03: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.787395] Linux agpgart interface v0.103
[    0.789424] loop: module loaded
[    0.789603] ata_piix 0000:00:1f.2: version 2.13
[    0.789736] ata_piix 0000:00:1f.2: MAP [ IDE IDE P1 P3 ]
[    0.790936] scsi host0: ata_piix
[    0.791071] scsi host1: ata_piix
[    0.791116] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    0.791118] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    0.791232] libphy: Fixed MDIO Bus: probed
[    0.791233] tun: Universal TUN/TAP device driver, 1.6
[    0.791285] PPP generic driver version 2.4.2
[    0.791339] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.791344] ehci-pci: EHCI PCI platform driver
[    0.791470] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.791477] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.795388] ehci-pci 0000:00:1d.7: cache line size of 4 is not supported
[    0.795402] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfdfff000
[    0.810474] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.810561] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 4.18
[    0.810565] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.810569] usb usb1: Product: EHCI Host Controller
[    0.810577] usb usb1: Manufacturer: Linux 4.18.0-16-generic ehci_hcd
[    0.810578] usb usb1: SerialNumber: 0000:00:1d.7
[    0.810695] hub 1-0:1.0: USB hub found
[    0.810703] hub 1-0:1.0: 8 ports detected
[    0.810917] ehci-platform: EHCI generic platform driver
[    0.810930] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.810933] ohci-pci: OHCI PCI platform driver
[    0.810944] ohci-platform: OHCI generic platform driver
[    0.810951] uhci_hcd: USB Universal Host Controller Interface driver
[    0.811041] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.811052] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.811058] uhci_hcd 0000:00:1d.0: detected 2 ports
[    0.811075] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff00
[    0.811131] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001, bcdDevice= 4.18
[    0.811133] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.811134] usb usb2: Product: UHCI Host Controller
[    0.811136] usb usb2: Manufacturer: Linux 4.18.0-16-generic uhci_hcd
[    0.811138] usb usb2: SerialNumber: 0000:00:1d.0
[    0.811240] hub 2-0:1.0: USB hub found
[    0.811248] hub 2-0:1.0: 2 ports detected
[    0.811428] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.811434] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.811439] uhci_hcd 0000:00:1d.1: detected 2 ports
[    0.811465] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fe00
[    0.811511] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001, bcdDevice= 4.18
[    0.811513] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.811515] usb usb3: Product: UHCI Host Controller
[    0.811517] usb usb3: Manufacturer: Linux 4.18.0-16-generic uhci_hcd
[    0.811518] usb usb3: SerialNumber: 0000:00:1d.1
[    0.811622] hub 3-0:1.0: USB hub found
[    0.811628] hub 3-0:1.0: 2 ports detected
[    0.811819] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.811825] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.811830] uhci_hcd 0000:00:1d.2: detected 2 ports
[    0.811853] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fd00
[    0.811902] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001, bcdDevice= 4.18
[    0.811904] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.811905] usb usb4: Product: UHCI Host Controller
[    0.811907] usb usb4: Manufacturer: Linux 4.18.0-16-generic uhci_hcd
[    0.811908] usb usb4: SerialNumber: 0000:00:1d.2
[    0.812006] hub 4-0:1.0: USB hub found
[    0.812012] hub 4-0:1.0: 2 ports detected
[    0.812188] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.812194] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.812200] uhci_hcd 0000:00:1d.3: detected 2 ports
[    0.812225] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fc00
[    0.812276] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001, bcdDevice= 4.18
[    0.812279] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.812280] usb usb5: Product: UHCI Host Controller
[    0.812282] usb usb5: Manufacturer: Linux 4.18.0-16-generic uhci_hcd
[    0.812283] usb usb5: SerialNumber: 0000:00:1d.3
[    0.812391] hub 5-0:1.0: USB hub found
[    0.812398] hub 5-0:1.0: 2 ports detected
[    0.812551] i8042: PNP: No PS/2 controller found.
[    0.812552] i8042: Probing ports directly.
[    0.812943] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.812953] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.813143] mousedev: PS/2 mouse device common for all mice
[    0.813324] rtc_cmos 00:01: RTC can wake from S4
[    0.813447] rtc_cmos 00:01: registered as rtc0
[    0.813469] rtc_cmos 00:01: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.813478] i2c /dev entries driver
[    0.813483] pcie_mp2_amd: AMD(R) PCI-E MP2 Communication Driver Version: 1.0
[    0.813566] device-mapper: uevent: version 1.0.3
[    0.813637] device-mapper: ioctl: 4.39.0-ioctl (2018-04-03) initialised: dm-devel@redhat.com
[    0.813657] ledtrig-cpu: registered to indicate activity on CPUs
[    0.814055] NET: Registered protocol family 10
[    0.819920] Segment Routing with IPv6
[    0.819948] NET: Registered protocol family 17
[    0.820001] Key type dns_resolver registered
[    0.820202] RAS: Correctable Errors collector initialized.
[    0.820257] microcode: sig=0x10676, pf=0x1, revision=0x60f
[    0.820297] microcode: Microcode Update Driver: v2.2.
[    0.820311] sched_clock: Marking stable (820292136, 0)->(903829883, -83537747)
[    0.820484] registered taskstats version 1
[    0.820497] Loading compiled-in X.509 certificates
[    0.824277] Loaded X.509 cert 'Build time autogenerated kernel key: ceadf4a2169e91fa82b127879b63b6598e2fd515'
[    0.824307] zswap: loaded using pool lzo/zbud
[    0.829644] Key type big_key registered
[    0.829650] Key type trusted registered
[    0.832303] Key type encrypted registered
[    0.832309] AppArmor: AppArmor sha1 policy hashing enabled
[    0.832318] ima: No TPM chip found, activating TPM-bypass! (rc=-19)
[    0.832323] ima: Allocated hash algorithm: sha1
[    0.832343] evm: Initialising EVM extended attributes:
[    0.832344] evm: security.selinux
[    0.832345] evm: security.SMACK64
[    0.832345] evm: security.SMACK64EXEC
[    0.832346] evm: security.SMACK64TRANSMUTE
[    0.832347] evm: security.SMACK64MMAP
[    0.832347] evm: security.apparmor
[    0.832348] evm: security.ima
[    0.832349] evm: security.capability
[    0.832350] evm: HMAC attrs: 0x1
[    0.832754]   Magic number: 11:221:311
[    0.832888] rtc_cmos 00:01: setting system clock to 2019-03-22 03:18:51 UTC (1553224731)
[    0.958703] ata2.00: HPA detected: current 488395055, native 488397168
[    0.958708] ata2.00: supports DRM functions and may not be fully accessible
[    0.958713] ata2.00: ATA-11: Samsung SSD 860 EVO 250GB, RVT01B6Q, max UDMA/133
[    0.958716] ata2.00: 488395055 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    0.961256] ata2.01: HPA detected: current 1953523055, native 1953525168
[    0.961261] ata2.01: ATA-9: ST1000DM003-1ER162, CC45, max UDMA/133
[    0.961265] ata2.01: 1953523055 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.966697] ata2.00: supports DRM functions and may not be fully accessible
[    0.977304] ata1.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.04, max UDMA/66
[    0.977309] ata1.01: ATAPI: IOMEGA  ZIP 250       ATAPI, 41.S, max UDMA/33, CDB intr
[    1.016939] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.04 PQ: 0 ANSI: 5
[    1.069639] sr 0:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.069642] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.069817] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.069876] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.074508] scsi 0:0:1:0: Direct-Access     IOMEGA   ZIP 250          41.S PQ: 0 ANSI: 5
[    1.101120] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.101267] scsi 1:0:0:0: Direct-Access     ATA      Samsung SSD 860  1B6Q PQ: 0 ANSI: 5
[    1.101397] ata2.00: Enabling discard_zeroes_data
[    1.101458] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    1.101474] sd 1:0:0:0: [sdb] 488395055 512-byte logical blocks: (250 GB/233 GiB)
[    1.101487] sd 1:0:0:0: [sdb] Write Protect is off
[    1.101489] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.101510] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.101586] scsi 1:0:1:0: Direct-Access     ATA      ST1000DM003-1ER1 CC45 PQ: 0 ANSI: 5
[    1.101656] ata2.00: Enabling discard_zeroes_data
[    1.101757] sd 1:0:1:0: Attached scsi generic sg3 type 0
[    1.101760] sd 1:0:1:0: [sdc] 1953523055 512-byte logical blocks: (1.00 TB/932 GiB)
[    1.101762] sd 1:0:1:0: [sdc] 4096-byte physical blocks
[    1.101774] sd 1:0:1:0: [sdc] Write Protect is off
[    1.101776] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[    1.101796] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.109197]  sdb: sdb1 sdb2
[    1.109243]  sdc: sdc1
[    1.109481] ata2.00: Enabling discard_zeroes_data
[    1.109538] sd 1:0:1:0: [sdc] Attached SCSI disk
[    1.110734] sd 1:0:0:0: [sdb] supports TCG Opal
[    1.110738] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.148028] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    1.188958] sd 0:0:1:0: [sda] Attached SCSI removable disk
[    1.193167] Freeing unused kernel image memory: 2456K
[    1.212026] Write protecting the kernel read-only data: 20480k
[    1.213243] Freeing unused kernel image memory: 2008K
[    1.214116] Freeing unused kernel image memory: 1792K
[    1.227895] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    1.227896] x86/mm: Checking user space page tables
[    1.241604] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    1.314326] usb 1-3: New USB device found, idVendor=058f, idProduct=6364, bcdDevice= 1.00
[    1.314329] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.314331] usb 1-3: Product: Mass Storage Device
[    1.314333] usb 1-3: Manufacturer: Generic
[    1.314334] usb 1-3: SerialNumber: 058F63646476
[    1.357791] Floppy drive(s): fd0 is 1.44M
[    1.379871] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.379885] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.379923] FDC 0 is a post-1991 82077
[    1.381509] r8169 0000:03:00.0 eth0: RTL8168c/8111c, 00:24:1d:1d:b7:33, XID 3c4000c0, IRQ 24
[    1.381512] r8169 0000:03:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.434327] r8169 0000:03:00.0 enp3s0: renamed from eth0
[    1.435538] gpio_ich: GPIO from 462 to 511 on gpio_ich
[    1.471629] random: fast init done
[    1.480828] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    1.481717] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    1.484491] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    1.644032] usb 4-1: new full-speed USB device number 2 using uhci_hcd
[    1.792019] tsc: Refined TSC clocksource calibration: 2499.999 MHz
[    1.792027] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x240938fe3e8, max_idle_ns: 440795307177 ns
[    1.792047] clocksource: Switched to clocksource tsc
[    1.838058] usb 4-1: New USB device found, idVendor=413c, idProduct=1002, bcdDevice= 2.00
[    1.838062] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.838066] usb 4-1: Product: Dell USB Keyboard Hub
[    1.838069] usb 4-1: Manufacturer: Dell
[    1.846095] hub 4-1:1.0: USB hub found
[    1.847056] hub 4-1:1.0: 3 ports detected
[    2.144017] usb 4-1.1: new full-speed USB device number 3 using uhci_hcd
[    2.294057] usb 4-1.1: New USB device found, idVendor=413c, idProduct=2002, bcdDevice= 2.00
[    2.294062] usb 4-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.294065] usb 4-1.1: Product: Dell USB Keyboard Hub
[    2.294069] usb 4-1.1: Manufacturer: Dell
[    2.308678] hidraw: raw HID events driver (C) Jiri Kosina
[    2.316581] usbcore: registered new interface driver usbhid
[    2.316583] usbhid: USB HID core driver
[    2.321508] hid-generic 0003:058F:6364.0001: hiddev0,hidraw0: USB HID v1.10 Device [Generic Mass Storage Device] on usb-0000:00:1d.7-3/input1
[    2.321793] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.0/0003:413C:2002.0002/input/input5
[    2.380149] hid-generic 0003:413C:2002.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-1.1/input0
[    2.380676] input: Dell Dell USB Keyboard Hub Consumer Control as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.1/0003:413C:2002.0003/input/input6
[    2.440139] input: Dell Dell USB Keyboard Hub System Control as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.1/0003:413C:2002.0003/input/input7
[    2.440207] hid-generic 0003:413C:2002.0003: input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-1.1/input1
[    2.660019] usb 4-2: new low-speed USB device number 4 using uhci_hcd
[    2.849059] usb 4-2: New USB device found, idVendor=0461, idProduct=4e22, bcdDevice= 1.00
[    2.849063] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.849067] usb 4-2: Product: USB Optical Mouse
[    2.849070] usb 4-2: Manufacturer: PixArt
[    2.864432] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:0461:4E22.0004/input/input8
[    2.864546] hid-generic 0003:0461:4E22.0004: input,hidraw3: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[    3.104018] usb 1-7: new high-speed USB device number 5 using ehci-pci
[    3.290329] usb 1-7: New USB device found, idVendor=041e, idProduct=4063, bcdDevice= 1.00
[    3.290333] usb 1-7: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    3.290336] usb 1-7: Product: VF0410 Live! Cam Video IM Pro
[    3.290340] usb 1-7: Manufacturer: Creative Technology Ltd
[    3.579534] usb-storage 1-3:1.0: USB Mass Storage device detected
[    3.579665] scsi host2: usb-storage 1-3:1.0
[    3.579782] usbcore: registered new interface driver usb-storage
[    3.581286] usbcore: registered new interface driver uas
[    4.608993] scsi 2:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    4.609731] scsi 2:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    4.610473] scsi 2:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
[    4.611224] scsi 2:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
[    4.612085] sd 2:0:0:0: Attached scsi generic sg4 type 0
[    4.612296] sd 2:0:0:1: Attached scsi generic sg5 type 0
[    4.612488] sd 2:0:0:2: Attached scsi generic sg6 type 0
[    4.612660] sd 2:0:0:3: Attached scsi generic sg7 type 0
[    4.617988] sd 2:0:0:2: [sdf] Attached SCSI removable disk
[    4.618732] sd 2:0:0:3: [sdg] Attached SCSI removable disk
[    4.620101] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[    4.622239] sd 2:0:0:1: [sde] Attached SCSI removable disk
[   33.792031] print_req_error: I/O error, dev fd0, sector 0
[   33.792080] floppy: error 10 while reading block 0
[   33.908028] print_req_error: I/O error, dev fd0, sector 0
[   33.908072] floppy: error 10 while reading block 0
[   34.024030] print_req_error: I/O error, dev fd0, sector 0
[   34.024078] floppy: error 10 while reading block 0
[   34.140033] print_req_error: I/O error, dev fd0, sector 0
[   34.140077] floppy: error 10 while reading block 0
[   35.248035] print_req_error: I/O error, dev fd0, sector 0
[   35.248083] floppy: error 10 while reading block 0
[   35.364032] print_req_error: I/O error, dev fd0, sector 0
[   35.364077] floppy: error 10 while reading block 0
[   35.480030] print_req_error: I/O error, dev fd0, sector 0
[   35.480078] floppy: error 10 while reading block 0
[   35.628031] print_req_error: I/O error, dev fd0, sector 0
[   35.628079] floppy: error 10 while reading block 0
[   35.732030] print_req_error: I/O error, dev fd0, sector 0
[   35.732078] floppy: error 10 while reading block 0
[   35.848031] print_req_error: I/O error, dev fd0, sector 0
[   35.848075] floppy: error 10 while reading block 0
[   35.964030] floppy: error 10 while reading block 0
[   36.080033] floppy: error 10 while reading block 0
[   36.120824] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   36.308942] systemd[1]: systemd 239 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[   36.328131] systemd[1]: Detected architecture x86-64.
[   36.330159] systemd[1]: Set hostname to <peyre>.
[   36.372927] systemd-fstab-generator[274]: Failed to create unit file /run/systemd/generator/media-floppy0.mount, as it already exists. Duplicate entry in /etc/fstab?
[   36.560629] systemd[1]: Reached target Remote File Systems.
[   36.560969] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   36.561120] systemd[1]: Listening on fsck to fsckd communication Socket.
[   36.561235] systemd[1]: Listening on Journal Socket (/dev/log).
[   36.561412] systemd[1]: Listening on Journal Audit Socket.
[   36.561545] systemd[1]: Listening on Journal Socket.
[   36.563789] systemd[1]: Mounting Kernel Debug File System...
[   36.599618] lp: driver loaded but no devices found
[   36.611974] ppdev: user-space parallel port driver
[   36.615166] parport_pc 00:04: reported by Plug and Play ACPI
[   36.615266] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   36.716758] lp0: using parport0 (interrupt-driven).
[   36.727024] imm: Version 2.05 (for Linux 2.4.0)
[   36.862782] systemd-journald[296]: Received request to flush runtime journal from PID 1
[   37.525510] intel_rng: FWH not detected
[   37.574593] leds_ss4200: no LED devices found
[   37.950192] media: Linux media interface: v0.10
[   37.982158] videodev: Linux video capture interface: v2.00
[   37.994009] random: crng init done
[   37.994012] random: 7 urandom warning(s) missed due to ratelimiting
[   38.100785] nouveau 0000:01:00.0: NVIDIA G94 (094100a1)
[   38.150879] uvcvideo: Found UVC 1.00 device VF0410 Live! Cam Video IM Pro (041e:4063)
[   38.171350] snd_hda_codec_realtek hdaudioC0D2: autoconfig for ALC883: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   38.171353] snd_hda_codec_realtek hdaudioC0D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   38.171355] snd_hda_codec_realtek hdaudioC0D2:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   38.171357] snd_hda_codec_realtek hdaudioC0D2:    mono: mono_out=0x0
[   38.171359] snd_hda_codec_realtek hdaudioC0D2:    dig-out=0x1e/0x0
[   38.171360] snd_hda_codec_realtek hdaudioC0D2:    inputs:
[   38.171363] snd_hda_codec_realtek hdaudioC0D2:      Rear Mic=0x18
[   38.171364] snd_hda_codec_realtek hdaudioC0D2:      Front Mic=0x19
[   38.171366] snd_hda_codec_realtek hdaudioC0D2:      Line=0x1a
[   38.171368] snd_hda_codec_realtek hdaudioC0D2:      CD=0x1c
[   38.189569] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   38.189654] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   38.189725] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   38.189802] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   38.208425] uvcvideo 1-7:1.0: Entity type for entity Extension 5 was not initialized!
[   38.208429] uvcvideo 1-7:1.0: Entity type for entity Extension 4 was not initialized!
[   38.208431] uvcvideo 1-7:1.0: Entity type for entity Processing 3 was not initialized!
[   38.208433] uvcvideo 1-7:1.0: Entity type for entity Camera 1 was not initialized!
[   38.208553] input: VF0410 Live! Cam Video IM Pro as /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/input/input13
[   38.208666] usbcore: registered new interface driver uvcvideo
[   38.208667] USB Video Class driver (1.1.1)
[   38.310598] usb 1-7: 3:1: cannot get freq at ep 0x84
[   38.315574] nouveau 0000:01:00.0: bios: version 62.94.82.00.00
[   38.323734] usb 1-7: Warning! Unlikely big volume range (=3072), cval->res is probably wrong.
[   38.323737] usb 1-7: [2] FU [Mic Capture Volume] ch = 1, val = 4608/7680/1
[   38.323967] usbcore: registered new interface driver snd-usb-audio
[   38.429083] nouveau 0000:01:00.0: fb: 512 MiB GDDR3
[   38.512615] intel_powerclamp: No package C-state available
[   38.777291] [TTM] Zone  kernel: Available graphics memory: 2019212 kiB
[   38.777294] [TTM] Initializing pool allocator
[   38.777299] [TTM] Initializing DMA pool allocator
[   38.777324] nouveau 0000:01:00.0: DRM: VRAM: 512 MiB
[   38.777325] nouveau 0000:01:00.0: DRM: GART: 1048576 MiB
[   38.777330] nouveau 0000:01:00.0: DRM: TMDS table version 2.0
[   38.777332] nouveau 0000:01:00.0: DRM: DCB version 4.0
[   38.777335] nouveau 0000:01:00.0: DRM: DCB outp 00: 02000300 00000028
[   38.777338] nouveau 0000:01:00.0: DRM: DCB outp 01: 01000302 00020030
[   38.777340] nouveau 0000:01:00.0: DRM: DCB outp 02: 04011310 00000028
[   38.777342] nouveau 0000:01:00.0: DRM: DCB outp 03: 02022322 00020010
[   38.777344] nouveau 0000:01:00.0: DRM: DCB conn 00: 00001030
[   38.777346] nouveau 0000:01:00.0: DRM: DCB conn 01: 00000100
[   38.777348] nouveau 0000:01:00.0: DRM: DCB conn 02: 00002261
[   38.793251] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   38.793253] [drm] Driver supports precise vblank timestamp query.
[   38.794700] nouveau 0000:01:00.0: DRM: MM: using CRYPT for buffer copies
[   38.861707] nouveau 0000:01:00.0: DRM: allocated 1280x1024 fb: 0x70000, bo 00000000f64a4e7c
[   38.861796] fbcon: nouveaufb (fb0) is primary device
[   38.909890] Console: switching to colour frame buffer device 160x64
[   38.911133] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[   38.916179] [drm] Initialized nouveau 1.3.1 20120801 for 0000:01:00.0 on minor 0
[   39.014508] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   39.317367] audit: type=1400 audit(1553224769.979:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=789 comm="apparmor_parser"
[   39.317372] audit: type=1400 audit(1553224769.979:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=789 comm="apparmor_parser"
[   39.317375] audit: type=1400 audit(1553224769.979:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=789 comm="apparmor_parser"
[   39.317378] audit: type=1400 audit(1553224769.979:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=789 comm="apparmor_parser"
[   39.323201] audit: type=1400 audit(1553224769.983:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine" pid=792 comm="apparmor_parser"
[   39.323208] audit: type=1400 audit(1553224769.983:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=792 comm="apparmor_parser"
[   39.323655] audit: type=1400 audit(1553224769.983:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=788 comm="apparmor_parser"
[   39.323658] audit: type=1400 audit(1553224769.983:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=788 comm="apparmor_parser"
[   39.330140] audit: type=1400 audit(1553224769.991:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/freshclam" pid=796 comm="apparmor_parser"
[   39.334096] audit: type=1400 audit(1553224769.995:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=798 comm="apparmor_parser"
[   98.364075] usb 4-2: USB disconnect, device number 4
[  100.124025] usb 4-2: new low-speed USB device number 5 using uhci_hcd
[  100.314091] usb 4-2: New USB device found, idVendor=0461, idProduct=4e22, bcdDevice= 1.00
[  100.314093] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  100.314095] usb 4-2: Product: USB Optical Mouse
[  100.314097] usb 4-2: Manufacturer: PixArt
[  100.329524] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:0461:4E22.0005/input/input14
[  100.329648] hid-generic 0003:0461:4E22.0005: input,hidraw3: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[  127.318649] kauditd_printk_skb: 44 callbacks suppressed
[  127.318651] audit: type=1400 audit(1553224857.979:56): apparmor="DENIED" operation="capable" profile="/usr/sbin/cupsd" pid=1061 comm="cupsd" capability=12  capname="net_admin"
[  127.370872] audit: type=1400 audit(1553224858.031:57): apparmor="DENIED" operation="open" profile="/usr/bin/freshclam" name="/etc/ssl/openssl.cnf" pid=1035 comm="freshclam" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[  127.389666] audit: type=1400 audit(1553224858.051:58): apparmor="DENIED" operation="capable" profile="/usr/bin/freshclam" pid=1035 comm="freshclam" capability=12  capname="net_admin"
[  127.390522] audit: type=1107 audit(1553224858.051:59): pid=1033 uid=106 auid=4294967295 ses=4294967295 subj==unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/systemd1" interface="org.freedesktop.systemd1.Manager" member="GetDynamicUsers" mask="send" name="org.freedesktop.systemd1" pid=1035 label="/usr/bin/freshclam" peer_pid=1 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=106 hostname=? addr=? terminal=?'
[  152.797767] vboxdrv: loading out-of-tree module taints kernel.
[  152.798239] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[  152.804325] vboxdrv: Found 2 processor cores
[  152.817278] vboxdrv: fAsync=0 offMin=0x2af offMax=0x203a
[  152.830714] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  152.872103] r8169 0000:03:00.0 enp3s0: link down
[  152.872199] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  152.873978] r8169 0000:03:00.0 enp3s0: link down
[  152.928681] vboxdrv: TSC mode is Synchronous, tentative frequency 2499999180 Hz
[  152.928683] vboxdrv: Successfully loaded version 5.2.18_Ubuntu (interface 0x00290001)
[  152.960819] VBoxNetFlt: Successfully started.
[  152.985214] VBoxNetAdp: Successfully started.
[  153.004533] VBoxPciLinuxInit
[  153.016250] vboxpci: IOMMU not found (not registered)
[  154.819786] r8169 0000:03:00.0 enp3s0: link up
[  154.819800] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  187.148073] usb 4-2: USB disconnect, device number 5
[  188.908024] usb 4-2: new low-speed USB device number 6 using uhci_hcd
[  189.097134] usb 4-2: New USB device found, idVendor=0461, idProduct=4e22, bcdDevice= 1.00
[  189.097139] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  189.097142] usb 4-2: Product: USB Optical Mouse
[  189.097146] usb 4-2: Manufacturer: PixArt
[  189.114734] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:0461:4E22.0006/input/input15
[  189.173402] hid-generic 0003:0461:4E22.0006: input,hidraw3: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[  249.396105] usb 4-2: USB disconnect, device number 6
[  251.156045] usb 4-2: new low-speed USB device number 7 using uhci_hcd
[  251.345162] usb 4-2: New USB device found, idVendor=0461, idProduct=4e22, bcdDevice= 1.00
[  251.345167] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  251.345171] usb 4-2: Product: USB Optical Mouse
[  251.345174] usb 4-2: Manufacturer: PixArt
[  251.360792] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:0461:4E22.0007/input/input16
[  251.420374] hid-generic 0003:0461:4E22.0007: input,hidraw3: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[  311.644072] usb 4-2: USB disconnect, device number 7
[  313.404026] usb 4-2: new low-speed USB device number 8 using uhci_hcd
[  313.593188] usb 4-2: New USB device found, idVendor=0461, idProduct=4e22, bcdDevice= 1.00
[  313.593193] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  313.593197] usb 4-2: Product: USB Optical Mouse
[  313.593201] usb 4-2: Manufacturer: PixArt
[  313.619363] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:0461:4E22.0008/input/input17
[  313.686093] hid-generic 0003:0461:4E22.0008: input,hidraw3: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[  373.900197] usb 4-2: USB disconnect, device number 8
[  375.652025] usb 4-2: new low-speed USB device number 9 using uhci_hcd
[  375.841233] usb 4-2: New USB device found, idVendor=0461, idProduct=4e22, bcdDevice= 1.00
[  375.841238] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  375.841242] usb 4-2: Product: USB Optical Mouse
[  375.841246] usb 4-2: Manufacturer: PixArt
[  375.861005] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:0461:4E22.0009/input/input18
[  375.920272] hid-generic 0003:0461:4E22.0009: input,hidraw3: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[  436.140080] usb 4-2: USB disconnect, device number 9
[  437.900027] usb 4-2: new low-speed USB device number 10 using uhci_hcd
[  438.094234] usb 4-2: New USB device found, idVendor=0461, idProduct=4e22, bcdDevice= 1.00
[  438.094239] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  438.094243] usb 4-2: Product: USB Optical Mouse
[  438.094246] usb 4-2: Manufacturer: PixArt
[  438.110889] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:0461:4E22.000A/input/input19
[  438.168279] hid-generic 0003:0461:4E22.000A: input,hidraw3: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[  498.388081] usb 4-2: USB disconnect, device number 10
[  500.148027] usb 4-2: new low-speed USB device number 11 using uhci_hcd
[  500.337260] usb 4-2: New USB device found, idVendor=0461, idProduct=4e22, bcdDevice= 1.00
[  500.337264] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  500.337268] usb 4-2: Product: USB Optical Mouse
[  500.337271] usb 4-2: Manufacturer: PixArt
[  500.354690] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:0461:4E22.000B/input/input20
[  500.412282] hid-generic 0003:0461:4E22.000B: input,hidraw3: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[  560.636092] usb 4-2: USB disconnect, device number 11
[  562.396030] usb 4-2: new low-speed USB device number 12 using uhci_hcd
[  562.586286] usb 4-2: New USB device found, idVendor=0461, idProduct=4e22, bcdDevice= 1.00
[  562.586292] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  562.586295] usb 4-2: Product: USB Optical Mouse
[  562.586299] usb 4-2: Manufacturer: PixArt
[  562.601899] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:0461:4E22.000C/input/input21
[  562.660285] hid-generic 0003:0461:4E22.000C: input,hidraw3: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.2-2/input0

```

You want details of the SMART data...?  Sigh, ok.

Temperature  41C / 106F   Self-assessment  Threshold not exceeded
Powered On  1 month and 11 days   Overall Assessment  Disk is OK

SMART Attributes
ID  Attribute  Value  Normalized  Threshold  Worst  Type  Updates  Assessment
5  Reallocated Sector Count  0 sectors  100 10 100 Pre-Fail Online OK
9 Power-On Hours 1 month and 11 days 99 0 99 Old-Age Online OK
12 Power Cycle Count 153 99 0 99 Old-Age Online OK
177 wear-leveling-count 1 99 0 99 Pre-Fail Online OK
179 used-reserved-blocks-total 0 100 10 100 Pre-Fail Online OK
181 program-fail-count-total 0 100 10 100 Old-Age Online OK
182 erase-fail-count-total 0 100 10 100 Old-Age Online OK
183 runtime-bad-block-total 0 100 10 100 Pre-Fail Online OK
187 Reported Uncorrectable Errors 0 sectors 100 0 100 Old-Age Online OK
190 Airflow Temperature 41C/106F 59 0 53 Old-Age Online OK
195 Hardware ECC Recovered 0 200 0 200 Old-Age Online OK
199 UDMA CRC Error Rate 0 100 0 100 Old-Age Online OK
235 Good Block Rate N/A 99 0 99 Old-Age Online OK
241 total-lbas-written N/A 99 0 99 Old-Age Online OK

---

### Post by TheFu on 2019-03-22
Should have said "relevant output"

Also, _code tags_ on the smart data would be helpful.  It didn't line up, so next to impossible to read. Stuff that is easier to read will get more eyes on it.

Does the posted **ls -l** show the file issue?   A random ls -l on just any directory isn't helpful.
Are all the file systems on the problem storage device read-only or just 1?  To check file systems, you can use the **df -Th** or **mount** or **lsblk** commands, then try to make a temp file on each file system.  Ignore 'loop' devices. Those aren't file systems on real storage.  The 'mount' command will show which are mounted as read-only and some other options, but the output is ugly.

dmesg - errors and warnings? This is all that I saw, but what did you see?
```

[   33.792031] print_req_error: I/O error, dev fd0, sector 0
[   33.792080] floppy: error 10 while reading block 0
[   33.908028] print_req_error: I/O error, dev fd0, sector 0
[   33.908072] floppy: error 10 while reading block 0
[   34.024030] print_req_error: I/O error, dev fd0, sector 0
[   34.024078] floppy: error 10 while reading block 0
[   34.140033] print_req_error: I/O error, dev fd0, sector 0
[   34.140077] floppy: error 10 while reading block 0
[   35.248035] print_req_error: I/O error, dev fd0, sector 0
[   35.248083] floppy: error 10 while reading block 0
[   35.364032] print_req_error: I/O error, dev fd0, sector 0
[   35.364077] floppy: error 10 while reading block 0
```
I'd disconnect the device claiming to be fd0.  I vaguely remember old tape drives used fd device drivers.

Same for applies any log file ... errors and warnings - if there are a few lines above or below those which seem related, please include them.  _Code tags_ are always best for any command output.  Things that should line up do.

To search all the current log files in /var/log/, I'd use this command:
```
egrep -i 'error|warn' /var/log/*g
```
That will show which files has what errors.  Then go into each of the RELEVANT files, find the error(s) and warning(s), then copy/paste the RELEVANT lines into a reply.

---

### Post by peyre on 2019-03-22
Well, GNOME Disks didn't give an easy way to save the SMART results to file so I had to type them, and I don't see a way to do tables here.  And didn't think to use spaces with the code tags.  So all right, here it is.  This is a little rough because the proportional characters don't WSYWIG to fixed-width, but I'm sure you'll be able to read it now.
```

    Temperature 41C / 106F                               Self-assessment Threshold not exceeded
    Powered On 1 month and 11 days                 Overall Assessment Disk is OK

    SMART Attributes
    ID    Attribute                    Value                        Normalized       Threshold     Worst    Type        Updates   Assessment
    5     Reallocated Sector Count       0 sectors                  100                10           100     Pre-Fail    Online       OK
    9     Power-On Hours                 1 month and 11 days        99                  0            99     Old-Age    Online       OK
    12   Power Cycle Count                 153                      99                 0             99     Old-Age    Online       OK
    177  wear-leveling-count                1                        99                  0           99     Pre-Fail    Online       OK
    179  used-reserved-blocks-total        0                        100                10           100     Pre-Fail    Online       OK
    181  program-fail-count-total           0                       100                10           100     Old-Age    Online      OK
    182  erase-fail-count-total               0                       100                10         100     Pre-Fail    Online      OK
    187  Reported Uncorrectable Errors 0 sectors                    100                 0           100     Old-Age    Online      OK
    190  Airflow Temperature              41C/106F                    59                  0          53     Old-Age     Online      OK
    195  Hardware ECC Recovered              0                      200                 0           200     Old-Age    Online      OK
    199  UDMA CRC Error Rate                   0                    100                  0           100     Old-Age   Online       OK
    235  Good Block Rate                       N/A                   99                   0           99     Old-Age    Online       OK
    241  total-lbas-written                     N/A                   99                  0           99     Old-Age    Online       OK 

```

---

### Post by peyre on 2019-03-22
There are no tape drives attached; there is an internal floppy drive.

I ran the **ls -l** in my home directory.  Don't know if that's the information you were looking for.

---

### Post by peyre on 2019-03-23
And here's the result of the **egrep** command you had me run.  Yow it's big.[ATTACH]282841[/ATTACH]

---

### Post by TheFu on 2019-03-23
Ok - I don't see anything wrong in the SMART data either.

TL;DR version ... 

I've never used "Disks" and never expected anyone to type more than 1 line - a command. If something seems harder than that, it probably isn't what someone here intended. **sudo smartctl -a /dev/sda**  If we ever ask for something that seems wasted, please, please, say something.  We don't know what you do and don't know, especially when you come across as someone with experience. Plus, I look at the "raw" values, since every vendor has different ways for the converted values to be used. The raw values tell so much more.

For example, a disk that gives me problems, but self-corrects:```

$ sudo smartctl -a /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-142-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     HGST MegaScale 4000
Device Model:     HGST HMS5C4040ALE640
Serial Number:    PL1331LAHGLR3H
LU WWN Device Id: **5 000cca 22ed4baf2**
Firmware Version: MPAOA580
User Capacity:    4,000,787,030,016 bytes [4.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5700 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (**current: 3.0 Gb/s**)
Local Time is:    Sat Mar 23 08:32:24 2019 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   134   134   054    Pre-fail  Offline      -       101
  3 Spin_Up_Time            0x0007   144   144   024    Pre-fail  Always       -       516 (Average 453)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       77
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   115   115   020    Pre-fail  Offline      -       41
  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       26402
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       74
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1156
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       1156
194 Temperature_Celsius     0x0002   206   206   000    Old_age   Always       -       29 (Min/Max 20/50)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
**199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       64**
```

Notice how I show the command and options, but remove the non-relevant stuff?  There's some interesting stuff in the header, so I included it.  Perhaps, the S/N or WWN shouldn't be posted - depends on what you consider too unique for privacy reasons.  When it comes to disks, for me, I don't see anything private in this data.  OTOH, I won't post any real NIC MACs, ever.  That is too unique and can be used over the network, with a little javascript, to specifically target a specific machine.

Everything is fine with that disk, except 199 - looks like a bad cable or bad SATA port. The HDD isn't connected at SATA-III speeds, just SATA-II, so there is definitely something wrong. But I can only see the issue in the "raw value" column.  The columns dumbed down for humans don't show any issue. It is a hassle to take that machine off line and because it has 8 disks, knowing exactly which 1 is the problem disk, is hard. I need to make little labels with the WWN (see the bold) and put those where I can see them without removing the HDD.

Here's a fairly new SSD, no issues being shown:```

$ sudo smartctl -a /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.15.0-46-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     Samsung SSD 860 EVO 500GB
Serial Number:    S3Z1NB0KC50463W
LU WWN Device Id: 5 002538 e40b49dbe
Firmware Version: RVT02B6Q
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   Unknown(0x09fc), ACS-4 T13/BSR INCITS 529 revision 5
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sat Mar 23 08:47:46 2019 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       351
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       45
177 Wear_Leveling_Count     0x0013   100   100   000    Pre-fail  Always       -       0
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   100   100   010    Pre-fail  Always       -       0
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   100   010    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   074   055   000    Old_age   Always       -       26
195 Hardware_ECC_Recovered  0x001a   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
235 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       4
**241 Total_LBAs_Written      0x0032   099   099   000    Old_age   Always       -       433071520**
```
No issues at all, with a real number for the 241 parameter, not some converted percentage.

Ok, onto the next post, but I have to do some maintenance around here this morning first.

---

### Post by TheFu on 2019-03-23
> **peyre said:**
> There are no tape drives attached; there is an internal floppy drive.

I ran the **ls -l** in my home directory.  Don't know if that's the information you were looking for.

When there is corruption in a file system, often times permissions cannot be displayed.  The rwx-r-xr-x stuff gets shown as ?????????? - literally.  I don't have any storage doing that now (that I know about), so I cannot show an example.  Searching online for 10 question marks is very hard.

---

### Post by TheFu on 2019-03-23
> **peyre said:**
> And here's the result of the **egrep** command you had me run.  Yow it's big.[ATTACH]282841[/ATTACH]

```
Result: hostbyte=DID_ERROR 
```
[https://askubuntu.com/questions/832394/what-does-this-error-mean](https://askubuntu.com/questions/832394/what-does-this-error-mean)

```
EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
```
So it looks like sdb is the issue, not sda. Well, and the floppy. I'd unplug the floppy drive, might just remove it, since it is broken.

If you removed all the unrelated issues (floppy disk, DNS, and virtualbox), the file isn't big.  Use grep -v {some regex here} to do that.
Also, the ZIP file is corrupted ...

I can see why you'd want to wipe the disk and start over with all those issues.  How'd the system get that way?  APT dependency problems have to be corrected quickly. They are like a little roof leak or seeing 1 rodent inside the house - it never gets better. Fix it immediately.

Anyways, backup everything and wipe.  I would still recommend using **apt-mark** to save a list of manually installed packages, so you can re-install them after a fresh install easily.  For some great tips on dealing with commands, google "*the art of the command line*" for a github repo.  Every time I re-read that, something new is learned.

If you don't actively use bluetooth, I'd remove those tools completely. Got hacked at a conference through bluetooth once. I remove it from all my Linux computers and disable it on Android since then. If you do use it, disable it when not in use. BT range is much farther than the claimed 30ft.

---

### Post by peyre on 2019-03-23
Wow, so that's what that ????????? was about.  You're right that I have *some* experience; I'm an IT guy and I'm pretty good with Windows, but my Linux experience is much less.  Somewhere above Noob but not approaching expert.  I've done work in the terminal but I spend most of my time in the GUI, so I know some of the commands, but the syntax for a lot of commands that require a bunch of switches etc. to execute (like **mount**) I always have to look up.  This **sudo smartctl -a /dev/sda** you've just given me is another good example.  Thanks for that btw.  Here's the result:
--Damn.  command not found.  And when I try to install smartmontools, I get "Unable to fetch some archives"

Might be related to the system drive being mounted read-only?

---

### Post by peyre on 2019-03-23
The floppy drive isn't bad, AFAIK; I've used it recently.  But worth a try.  I shut down and pulled the cable out of the back of the floppy drive (it's an internal one), and I'm still getting the screen full of **print_req_error: I/O error, dev fd0, sector 0**.  wth?  There *is* no floppy drive, Xubuntu!

Still having to sign on at the terminal, getting the same read-only errors, and not going to the GUI.

---

### Post by peyre on 2019-03-23
> **TheFu said:**
> I can see why you'd want to wipe the disk and start over with all those issues.  How'd the system get that way?  APT dependency problems have to be corrected quickly. They are like a little roof leak or seeing 1 rodent inside the house - it never gets better. Fix it immediately.
Huh, didn't know that.  Maybe I'll have to make a habit of repairing packages from time to time just as a periodic maintenance thing.  How'd my system get this way?  Dunno.  I just tried to boot up one morning and it started doing this.  Everything was routine the night before, as I recall.

> **TheFu said:**
> Anyways, back up everything and wipe.  I would still recommend using **apt-mark** to save a list of manually installed packages, so you can re-install them after a fresh install easily.  For some great tips on dealing with commands, google "*the art of the command line*" for a github repo.  Every time I re-read that, something new is learned.

If you don't actively use bluetooth, I'd remove those tools completely. Got hacked at a conference through bluetooth once. I remove it from all my Linux computers and disable it on Android since then. If you do use it, disable it when not in use. BT range is much farther than the claimed 30ft.
After all this, I'm relieved to hear you recommend I wipe and reinstall.  That, at least, I can do for myself easily, even if it's a pretty tedious process.  My laptop I don't mind redoing from scratch, but my desktop has so much customization that I'm always leery of doing it.  But with all this trouble the current install is giving me, that looks like the path of least resistance for a change.  I'll get started on it.  Thanks for your time and assistance on that.  And the advice re. bluetooth.  I'll look into disabling that on my laptop, and I'll check out the command line instructions you mentioned while my main system is installing.

---

### Post by peyre on 2019-03-24
I wiped the drive and started the process of reinstalling everything.  Everything went pretty well, including watching some Star Trek and a YouTube video with my son (I'm introducing him to TOS, woohoo!).  But then I went to watch a movie I'd saved to ISO.  It opened to the main screen, then the audio caught.  You know, stuck repeating a note over and over.  I hit reset and it rebooted to a screen showing several lines saying:
/dev/sdb1: Clearing orphaned inode  ###### (uuid ...
Then
You are in emergency mode. After logging in, type "journalctl -xb" to view
system logs, "systemctl reboot" to reboot, "systemctl default" or "exit"
to boot into default mode.
Press Enter for maintenance
(or press Ctrl-D ton continue):
Reloading system manager configuration
[   ###.######## systemd-fstab-generator[738]: Failed to create unit file /run/systemd/generator/media-floppy0.mount, as it already exists. Duplicate entry in /etc/fstab?
Starting default target
You are in emergency mode. After logging in, type "journalctl -xb" to view
system logs, to reboot, "systemctl default" or "exit"
to boot into default mode.
Press Enter for maintenance
(or press Ctrl-D ton continue):

A further reset (out of habit) returned:
               ############ files, #########/################ blocks
[  ###########] systemd-fstab-generator[226]: Failed to create unit file run/systemd/generator/media-floppy.mount, as it already exists. Duplicate entry in /etc/fstab?
[  ###########] systemd[220]: /lib/systemd/system-generators/systemd-fstab-generator failed with exit status 1.
[  ###########] usb 1-7: 3:1: cannot get freq at ep 0x84
You are in emergency mode. After logging in, type "journalctlctl -xb" or "exit" 
to boot into default mode.
Presss Enter for maintenance.

---

### Post by TheFu on 2019-03-24
Did you fix the fd0 line(s) in the fstab?  Just comment those out.  Use **sudoedit** to edit system files.

I don't use GUIs much on Linux.  Servers don't have a GUI and the command line method works on my local system or the systems 5K miles away. No need to learn 2 methods, since the CLI version works everywhere. Handy if you use a VPS or just have a server in the basement.  ssh is how unix people manage any system they aren't currently, physically, on.

Every command has a manpage already on the box.  You can search all the manpages to find the right command - to search just the 1-line cmd description use **apropos**. To search all the text is more complex, but that's why we have aliases and scripts.  There are powerful text processing, searching, modification tools on every Linux/Unix system.  Learn to use those, via *The Scripts*, like you've learned to use *The Force*. With *The Scripts*, we have a powerful ally. ;)

I got a new laptop about a month ago.  Took about 45 min to move over everything from the prior laptop - all settings, customizations, keyboard accel setup, crontabs, other automations.  It is exactly "My" computer. No more. No less.  No huge hassle. Besides putting the settings, data, and other things back, loading the previously installed packages is where **apt-mark** helps. This was from a fresh install, using customized, encrypted, storage.  As long as the files appear to be in the same places (directories, owners, permissions), the underlying storage stuff can be different.

---

### Post by peyre on 2019-03-24
I remmed out the fd0 line in fstab and rebooted.  Back in emergency mode.

---

### Post by peyre on 2019-03-24
Ok, I finally managed to get smartmontools installed.  Here are the results of **sudo smartctl -a /dev/sdb** (while running from a Xubuntu DVD):
```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-4.15.0-20-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     Samsung SSD 860 EVO 250GB
Serial Number:    S3YHNX0K906237K
LU WWN Device Id: 5 002538 e4073bbe2
Firmware Version: RVT01B6Q
User Capacity:    250,058,268,160 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   Unknown(0x09fc) (unknown minor revision code: 0x005e)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sun Mar 24 17:35:32 2019 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(    0) seconds.
Offline data collection
capabilities: 			 (0x53) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  85) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1035
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       160
177 Wear_Leveling_Count     0x0013   099   099   000    Pre-fail  Always       -       2
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   100   100   010    Pre-fail  Always       -       0
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   100   010    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   070   053   000    Old_age   Always       -       30
195 Hardware_ECC_Recovered  0x001a   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
235 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       9
241 Total_LBAs_Written      0x0032   099   099   000    Old_age   Always       -       1055312731

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1009         -
# 2  Extended offline    Completed without error       00%      1004         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```
I'm not sure what to make of it!  I must be reading it wrong because it looks to me like I have a bunch of counter values way too high, but failures registered.  I must be reading it wrong.

---

### Post by TheFu on 2019-03-24
I think the wear_leveling is the only issue in there.  [https://superuser.com/questions/1037644/samsung-ssd-wear-leveling-count-meaning](https://superuser.com/questions/1037644/samsung-ssd-wear-leveling-count-meaning) has explanations, but they seem exactly backwards for my SSD and probably yours too.  The raw value of "2" means 98% left and available, methinks.

You can look up the #241 specs inside the drive sheet.  Is that number over their TBW warranty? Looks like about 1TB. Most SSDs have a 100+ TBW warranty. I think the 860 EVO TBW is 150+ (don't quote me, i didn't look at the 250G size SSDs at all), so you should be fine.  I have an 860 EVO too, BTW. 

I would look at the disk controller or motherboard for problems at this point.  There's a 78% chance that this SSD is fine.  Try a different SATA port and different SATA cable.  If you can, use a different disk controller - my MB has 2 different SATA controllers - one handles only SATA disks and the other handles SATA or NVMe storage, by disabling the SATA ports on the controller when NVMe is enabled in the BIOS.  I've seen older MBs that had SATA ports 1-4 on a jmicron disk controller and SATA ports 5-6 on a Maxell.  You  can check this using **sudo lshw -C storage** Check out the PCI-bus info ... 

And it could always be a failing PSU or PSU cable.

---

### Post by peyre on 2019-03-24
Hm, I changed the SATA cable and plugged it into a different SATA port, SATA3 I think.  I'm getting the same issue again.  Here's the result of **lsw -C storage** for the scsi ports:
```

*-scsi:0
  physical id: 1
  logical name: scsi0
  capabilities: emulated
*- scsi:1
  physical id: 2
  logical name: scsi2
  capabilities: emulated
*- scsi:2
  physical id: 3
  logical name: scsi3
  capabilities: emulated
*- scsi:3
  physical id: 5
  logical name: scsi5
  capabilities: scsi-host
  configuration:driver=ppa

```

---

### Post by TheFu on 2019-03-24
That output doesn't look anything link what I see here on multiple systems. Did you run the exact command I posted?  Showing the exact command in the output is important, BTW.

---

### Post by peyre on 2019-03-24
Oh!  You're right to ask; I see I made a typo in my post.  The command I entered was **lshw -C storage** (no sudo because I was running as root).

---

### Post by TheFu on 2019-03-25
But the answer doesn't look anything like what I see on multiple hosts.
```
$ sudo lshw -C storage
  *-usb:0                 
       description: Mass storage device
       product: USB to ATA/ATAPI Bridge
       vendor: JMicron
       physical id: 3
       **bus info: usb@1:3**
       logical name: scsi13
       version: 1.00
       serial: DA3680890FFF
       capabilities: usb-2.00 scsi emulated scsi-host
       configuration: driver=usb-storage maxpower=2mA speed=480Mbit/s
  *-storage
       description: SATA controller
       product: Advanced Micro Devices, Inc. [AMD]
       vendor: Advanced Micro Devices, Inc. [AMD]
       physical id: 0.1
       [B]bus info: pci@0000:01:00.1
[/B]       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list rom
       configuration: driver=ahci latency=0
       resources: irq:46 memory:f7780000-f779ffff memory:f7700000-f777ffff
```

---

### Post by peyre on 2019-03-25
Hm.  I'll rerun it this evening.

---

### Post by peyre on 2019-03-25
Ok, this time I booted from the hard drive and ran **lshw -C storage > /home/leon/Storage/lshw.txt** (~/Storage is where my mechanical drive is mounted in fstab).  Here's the full text:
```

  *-usb:0
       description: Mass storage device
       product: Mass Storage Device
       vendor: Generic
       physical id: 3
       bus info: usb@1:3
       logical name: scsi4
       version: 1.00
       serial: 058F63646476
       capabilities: usb-2.00 scsi emulated scsi-host
       configuration: driver=usb-storage maxpower=250mA speed=480Mbit/s
  *-ide:0
       description: IDE interface
       product: 82801G (ICH7 Family) IDE Controller
       vendor: Intel Corporation
       physical id: 1f.1
       bus info: pci@0000:00:1f.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: ide isa_compatibility_mode_controller__supports_both_channels_switched_to_pci_native_mode__supports_bus_mastering bus_master
       configuration: driver=ata_piix latency=0
       resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f900(size=16)
  *-ide:1
       description: IDE interface
       product: NM10/ICH7 Family SATA Controller [IDE mode]
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm pci_native_mode_controller__supports_both_channels_switched_to_isa_compatibility_mode__supports_bus_mastering bus_master cap_list
       configuration: driver=ata_piix latency=0
       resources: irq:19 ioport:f800(size=8) ioport:f700(size=4) ioport:f600(size=8) ioport:f500(size=4) ioport:f400(size=16)
  *-scsi:0
       physical id: 1
       logical name: scsi0
       capabilities: emulated
  *-scsi:1
       physical id: 2
       logical name: scsi2
       capabilities: emulated
  *-scsi:2
       physical id: 3
       logical name: scsi3
       capabilities: emulated
  *-scsi:3
       physical id: 5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=ppa

```

---

### Post by peyre on 2019-03-25
In the meantime, I have an old 500GB mechanical drive (I think it was the original system drive this machine came with!).  I've swapped it out for my SSD and am installing Xubuntu on that, to see if the problem continues with a different drive.

---

### Post by peyre on 2019-03-26
Well!  That's interesting.  I installed Xubuntu on that mechanical drive, installed updates and added the line to fstab to mount my second drive as /home/leon/Storage and the ppa and imm lines from /etc/modules to enable the zip drive.  Rebooted, and experienced the same problem.  I removed both, rebooted, and everything normal.  I added one back, rebooted, fine.  Added the other back, rebooted, still fine.  wth??

I switched the drives back, and am now on the SSD again.  Booted, got the error.  Removed the lines from /etc/modules, rebooted, same problem.  Remmed out the line in /etc/fstab (which I've had for ages!), and now my system boots normally.  What the?

---

### Post by TheFu on 2019-03-26
Reboots and full, power off, are different for some hardware.

IDE?!!!!!   Dude.  It's passed time.  Take that MB out back and shoot it in the head. Be kind.  ;)  A MB that old just doesn't have the same bus throughput capabilities that a $40 MB today does.  Throughput since 2013 is totally different from all prior hardware.

---

### Post by peyre on 2019-03-26
Ha, now you can see why I wanted to get my desktop back up and running - my laptop's even older. ;)

lol...I know it's an old machine.  It does everything I need though; the only thing is it's a little pokey when I do video editing in Flowblade.

Yes, I also did a cold bootup this morning, and it came up just fine.  I think we might be good, after all this.

---

### Post by TheFu on 2019-03-26
Heck, a Rock64Pro or Odroid for $60-$80 might be faster than something that old.  
[https://ameridroid.com/products/odroid-n2](https://ameridroid.com/products/odroid-n2)
[https://www.pine64.org/?page_id=61454](https://www.pine64.org/?page_id=61454)

I've seen Ryzen 5 1600s for $80 *this week*!  A cheap MB, 4G of DDR4 and you have a system to put into your existing case, reuse the PSU, monitor, GPU, keyboard and SSD.  That IDE HDD will need an adaptor.  That CPU is 12,200 passmarks and 65W peak power draw.  So, for under $200 total, you have a mid-high end computer.

Will it support ZIP drives? Doubtful. They don't include floppy drive controllers anymore.

Also - your discussion about what you did is extremely vague. I have no idea what really happened there. Something with modules and lines in the fstab, but no clue what or which.

---

### Post by peyre on 2019-03-29
Sorry about the vagueness, TheFu.  You know how it is sometimes when you get troubleshooting, you start trying things and it's easy to lose track of what you did when something finally works.  I think the problem was in my fstab all along; when I made changes I didn't change them right.  I'll show it below.

Thanks, but again, at present the system is working well for me.  Outside of Flowblade, I don't really need a lot of processing power, plus this system has some overclocking options I'll start to look into when I notice it's lagging behind my expectations.  With an SSD, the interface is snappy, which is what I look for in terms of speed (whereas my wife doesn't care about that; she worries about her system being able to handle tasks in Photoshop and all that kind of thing, so she has the newer, more powerful computer).  Don't worry, you're not seeing an IDE hard drive; ther's an ATAPI zip drive and I think also the optical drive is on IDE.  (The internal zip drive is starting to give me some trouble so I think it might be on the verge of failing, which is what made me dig out that old parallel drive. Yeah, I know zip drives are way out of date, but I use them to take files to and from work all the time and I have all the equipment already, so they're still useful.)

This is my fstab at present; remming out the line /dev/fd0 seems to have fixed it (but I could swear I tried that earlier--maybe that plus the reinstall from scratch fixed this, I dunno):
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=650ff563-e1c6-4542-b73f-a12b66b4d9b3 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# mount sdc1 on /data
# UUID="ea63af7b-4174-4dfc-956d-fd97da4e63b3"  /home/leon/Storage             ext4    defaults  0       2
# /dev/fd0 /media/floppy0 auto rw,user,exec,utf8,noauto,x-gvfs-show 0 0
/dev/fd0 /mnt/fd0 auto rw,user,sync,noauto,exec,umask=0,x-gvfs-show 0 0
/dev/disk/by-uuid/30C8-ECED /mnt/30C8-ECED auto rw,user,sync,noauto,exec,umask=0,x-gvfs-show 0 0

```

---

### Post by peyre on 2019-03-29
Oh I should mark this as solved, since I've been up and running without trouble for several days.  Not trying to shut down discussion; I just don't want to not tie up the loose end on this one.

Edit: It's happening again.  And now it always boots up as a read-only file system.

---

### Post by #&amp;thj^% on 2019-04-11
Now you should have back-ups in place, right?
Have you or can you at this point get to a tty session?
if so try to remove the offending line:
```
 sudo rm -rf /etc/.fstab.swp
```
Might be wise here to copy your "/etc/fstab" file first.
```
sudo cp /etc/fstab Documents
```
Also I see where you have errors with any attempt to edit fstab:
Try this one:
```
sudoedit /etc/fstab
```
Or even this:
```
sudo -e /etc/fstab
```
Good Luck :)

---

### Post by peyre on 2019-04-11
Oh, here's the content of my fstab.  The only line I've added is the one mounting /home/leon/Storage, and I've been trying to rem it out or delete it, but can't.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
/swapfile                                 none            swap    sw              0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# mount sdc1 on /data
# UUID="ea63af7b-4174-4dfc-956d-fd97da4e63b3"  /home/leon/Storage             ext4    defaults  0       2
UUID="7953d544-33e7-43f9-9b98-2ecb3479cd19" /home/leon/Storage ext4 defaults 0 2
# /dev/fd0 /media/floppy0 auto rw,user,exec,utf8,noauto,x-gvfs-show 0 0
/dev/fd0 /mnt/fd0 auto rw,user,sync,noauto,exec,umask=0,x-gvfs-show 0 0
/dev/disk/by-uuid/30C8-ECED /mnt/30C8-ECED auto rw,user,sync,noauto,exec,umask=0,x-gvfs-show 0 0
/dev/sdd /mnt/sdd auto rw,user,sync,noauto,exec,umask=0,x-gvfs-show 0 0
```

---

### Post by peyre on 2019-04-11
Thanks for responding, 1fallen!  Turns out I can't do the things you suggested because for some reason I can't fathom, Xubuntu mounts my main HD as read-only.  I have managed to get it mounted rw when running a live DVD, so I remmed out the /home/leon/Storage line and rebooted, but it's still coming up the same way.  Now I'm still puzzled - that should have worked!

---

### Post by #&amp;thj^% on 2019-04-11
One last thing to try with the older hardware your using, unplug both cables from the hardrive that has the os on it, power on with the cables still disconnected,power off. Now hook your cables back up and power on again.
I know this sounds silly but it worked for me and others.

---

### Post by peyre on 2019-04-11
I sort of did that before, but what the hey, worth a shot.  The strange thing though is that earlier, when I swapped out my SSD for a 500GB HDD I had in storage, it did the same thing.  So...

Uh oh, now it won't boot from the drive at all.  It starts up, then sits at "Boot from CD/DVD :"  I can boot from a Xubuntu DVD, but it doesn't want to boot from the hard drive.  I can still mount and navigate the SSD though, once it boots from DVD.

---

### Post by #&amp;thj^% on 2019-04-11
If you can get to the BIOS make sure you show the Drive with OS installed on, and make sure you allow it to boot from that drive.
Also check to be sure the connections to the drive are snug tight in place.
Sounds to me like Old Trusty (Your computer) is beginning to fail.:(

---

### Post by peyre on 2019-04-12
I'm starting to lean toward that conclusion myself.  It's a shame; it's been a great computer, does everything I need, and still has some expansion potential in that I can overclock it if I need extra processing power from it.  Plus all our money is going into the house right now and we really don't need an extra expense.  Well, we'll see.  I'll see about getting into the BIOS tomorrow morning (I'll be working late tonight).

---

### Post by #&amp;thj^% on 2019-04-12
> **peyre said:**
> I'm starting to lean toward that conclusion myself.  It's a shame; it's been a great computer, does everything I need, 
I can definitely relate to that I built 2 towers about 11 years ago, and when they died, I think I actually mourned the loss. :o
Best Regards

---

### Post by peyre on 2019-04-13
Ok, Saturday morning, and checking out what you suggested.  I can get into the BIOS, and I see the boot drive here.  It shows as the "IDE Channel 1 Master".  Should that show as IDE, not SATA?

The boot order shows as 1 Floppy, 2 CDROM, 3 Hard Disk, just like it should.  That's too bad; would be nice if it had been that simple.

Ok, I unplugged the drive altogether.  I connected it to a different SATA port, using a different SATA cable, and now it's able to boot again...but I'm back to booting to a command line.  Any suggestions or ideas?

That includes, of course, the possibility that the tower could be on its last legs, if you think that's the case.  I just hesitate to take action on that until I've exhausted my options.

---

### Post by peyre on 2019-04-18
Interesting.  Playing with it over several days, I think "Old Faithful" might still be in good working order.  I can boot from lots of different live disks, and I had an old laptop hard drive sitting around with a fresh install of Xubuntu on it, plugged it in, and it booted just fine.  Looking back on it, my system went down after I messed around with fstab.  Maybe if I just leave fstab alone I'll be good.  So I've rebuilt my system from scratch on the SSD again and am restoring and fine-tuning it again.  So far so good.  Keeping my fingers crossed.

---

