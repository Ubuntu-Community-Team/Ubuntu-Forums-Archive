---
title: "Smartmontools doesn't count Load Cycle"
date: 2008-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cisoprogressivo on 2008-10-15
My XPS M1330 is affected by Load Cycle Bug, but i can't count it with smartmoontool.
This is my output:
```
$ sudo smartctl -a /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM400LI
Serial Number:    S1HNJ10Q900182
Firmware Version: 2TF00_00
User Capacity:    400,088,457,216 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Wed Oct 15 22:56:50 2008 CEST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

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
data collection: 		 ( 130) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
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
recommended polling time: 	 ( 130) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       3500
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       3194
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       92
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       151
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       64
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       14
194 Temperature_Celsius     0x0022   103   097   000    Old_age   Always       -       45 (Lifetime Min/Max 14/47)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       5232
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       179
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       433
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         2         -
# 2  Short offline       Completed without error       00%         1         -
# 3  Short offline       Completed without error       00%         0         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

As you can see, the 193 value (Load Cycle Count) is not present.
Why is this happening?

---

### Post by dizcrypt on 2008-10-16
The answer is simple: your Samsung HDD does not support this attribute.
Check "4 Start_Stop_Count" instead. As you can see your drive performed 3194 start / stop cycles during only 92 hours of work.

---

### Post by cisoprogressivo on 2008-10-16
Thank you for your help.
I supposed it but I hoped it was not the problem.
Can you teach me how to study the Start_Stop_Count value?
Is it the same of the Loday_cycle_count?
Thank you again, and sorry for my bad english.

---

### Post by dizcrypt on 2008-10-16
The idea is the same as with Load Cycles. Doing it too often will shorten drive's life.
To solve the problem follow the advices for Load Cucles. I mean creation of a special script with hdparm -h 254. There was a topic regarding this in "Hardware & Laptops" subforum.

---

