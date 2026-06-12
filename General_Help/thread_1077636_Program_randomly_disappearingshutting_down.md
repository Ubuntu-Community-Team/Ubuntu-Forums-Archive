---
title: "Program randomly disappearing/shutting down"
date: 2009-02-22
forum: General Help
---

### Post by poolarinn on 2009-02-22
Hi there. I have very strange problem with my Ubuntu 8.10 system. I installed it few days ago on my IBM Thinkpad T43p laptop, along with Windows XP media center(on seperate partition).

Anyway, the problem I have is that sometimes the program I am using suddenly shut down without a warning, and often I can't even open the program again, or any other program. 

It has happened often with Firefox,and few times with other programs(including Terminal and Processor) sometimes I can open it again but sometimes I have to restart the computer to be able to open it. 

Sometimes when I try to open program, for example terminal, it loads like usually but then immediately shuts down again so I can't use it.

I would be very thankful if someone has the solution for my problem.

---

### Post by deepclutch on 2009-02-22
Is it Like a freezing of whole Desktop?
I doubt it may be your laptop's hard disk which is nearing its service cycle.if possible ,install "smartmontools" and run "sudo smartctl -a /dev/sdx" /dev/sdx is your harddisk(use sudo fdisk -l to find the hdd device name).This happened to me twice due to my 2 hard disks failed or nearing failure.
sometimes ,it may be a corrupted partition due to a improper shutdown(more unlikely!).
--
EDIT:oh! you may be having windows installed?then get some SMART Monitoring tool for harddisks installed and verify that your harddisk is fine :)

---

### Post by poolarinn on 2009-02-22
I have had some problems with my hard disk in windows (it's not supported by IBM, the type is WDC WD2500BEVE-0). 

But when i write "sudo smartctl -a /dev/sdx" I get this message:

[I]"smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/sdx failed: No such file or directory
[/I]

I tried to find some program in Windows to do this SMART thing, but the internet connection is not working there :S

---

### Post by deepclutch on 2009-02-22
I said , /dev/sdx  where sdx means your harddisk number.you run "sudo fdisk -l" and see what your harddisk name is ?if it lists partitions as "/dev/sda1 ..2 ..3 etc " then ,replace /dev/sdx with /dev/sda .OK? try again :)
```
 sudo smartctl -a /dev/sda
```

---

### Post by poolarinn on 2009-02-22
This is the information I get from the SMARTON tool in Linux:


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio family
Device Model:     WDC WD2500BEVE-00WZT0
Serial Number:    WD-WXE308E34523
Firmware Version: 01.01A01
User Capacity:    250.059.350.016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 22 21:59:22 2009 CET
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
data collection: 		 (8760) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 106) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x203f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   186   186   021    Pre-fail  Always       -       1658
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       436
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       840
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       188
184 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       48
193 Load_Cycle_Count        0x0032   187   187   000    Old_age   Always       -       40097
194 Temperature_Celsius     0x0022   110   101   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        20         -

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

---

### Post by deepclutch on 2009-02-22
so ,your harddisk is OK.It seems to me some problems with distro installation.also ,show me the output of "free -m" from terminal.

---

### Post by poolarinn on 2009-02-22
here is what i get when I write free-m:

             total       used       free     shared    buffers     cached
Mem:          1008        785        223          0         32        359
-/+ buffers/cache:        393        614
Swap:         1921          0       1921

---

### Post by deepclutch on 2009-02-23
what is your graphics card?now what left to check is memory corruption and/or graphics card with buggy driver.

---

### Post by Kevbert on 2009-02-23
Please try running memtest from the grub boot menu for a couple of passes.

---

### Post by poolarinn on 2009-02-23
> **deepclutch said:**
> what is your graphics card?now what left to check is memory corruption and/or graphics card with buggy driver.

How do I check the card for memory corruption? And how do I install the drivers I need, if that is the case?
My graphic card is: 

GRAPHIC CARD
VGA controller
ATI Technologies Inc M24GL [Mobility FireGL V3200] (rev 80)
Subsystem: IBM Device 0570

> Please try running memtest from the grub boot menu for a couple of passes. 
How exactly do I run this memtest?

---

### Post by deepclutch on 2009-02-23
In the grub menu ,it will be available? "memtest " will be shown.
--
your ati graphics card ,will need a proper driver.you may be using free driver?
It may be the reason.
[http://ubuntuforums.org/showthread.php?t=718089](http://ubuntuforums.org/showthread.php?t=718089)
and do try the method explained here:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by Kevbert on 2009-02-23
When you first turn on the computer you should get a menu which gives you the options to boot into XP or Ubuntu. It also has a menu option called 'Ubuntu 8.10, memtest86+'. Select this option to perform an intensive memory test.
You should not get any errors at all. You may get errors even if Windows seems to run OK (but crashes very occasionally for some unknown reason).

---

### Post by poolarinn on 2009-02-23
Okay, I did this memory test and got 29.000 errors(don't remember the exact number). What do all those errors mean?

I also noticed that my Graphic Card drivers weren't installed, although I thought I had them installed(I have the drivers now).

---

### Post by deepclutch on 2009-02-23
that means you need to replace your memory cards.what memtest does?
> **Memtest86+** is [software]("http://en.wikipedia.org/wiki/Software") designed to [stress test]("http://en.wikipedia.org/wiki/Stress_test") an [86-compatible]("http://en.wikipedia.org/wiki/X86_architecture") computer's [random access memory]("http://en.wikipedia.org/wiki/Random_access_memory") (RAM) for errors. It tries to verify that the RAM will accept and correctly retain arbitrary patterns of data written to it.
[http://en.wikipedia.org/wiki/Memtest86%2B](http://en.wikipedia.org/wiki/Memtest86%2B)
if you got 2 memory cards ,then try removing one of them and boot the system ,it may not start -that means that one memory card has gone-so use the other memory card(trial and error).

---

### Post by poolarinn on 2009-02-24
okay, thank you for that information;)

---

