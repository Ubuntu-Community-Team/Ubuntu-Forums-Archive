---
title: "ubuntu disk check tools"
date: 2010-03-06
forum: Desktop Environments
---

### Post by Mia1990 on 2010-03-06
Hello i am looking for some disk check tools in ubuntu the check icon on gnome keeps saying there are errors on my disk but i found that it has a bug were it will say that for no reason is there any disk check other then this and how would i run a fs check from the live cd thanks
> sudo touch /forcefsck  

---

### Post by psusi on 2010-03-06
Install the smartmontools package and run sudo smartctl -A /dev/sda and post the results.

---

### Post by Mia1990 on 2010-03-06
Here you go

> mia@mia:~$ sudo smartctl -A /dev/sda
[sudo] password for me: 
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   220   218   063    Pre-fail  Always       -       9101
  4 Start_Stop_Count        0x0032   250   250   000    Old_age   Always       -       6717
  5 Reallocated_Sector_Ct   0x0033   240   240   063    Pre-fail  Always       -       133
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   250   235   187    Pre-fail  Always       -       34709
  9 Power_On_Minutes        0x0032   186   186   000    Old_age   Always       -       284h+50m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   243   243   000    Old_age   Always       -       4233
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   253   253   000    Old_age   Always       -       51
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       22845
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   253   253   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0008   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       8
202 TA_Increase_Count       0x000a   253   252   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       2
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   253   253   000    Old_age   Offline      -       0
 99 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
100 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
101 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0

mia@mia:~$ 

---

### Post by psusi on 2010-03-06
Looks like you have had 133 bad sectors reallocated.  Not so good.  You might want to force a full media test with sudo smartctl -t long /dev/sda.

---

### Post by m4tic on 2010-03-11
have u tried the e2fsck tool

---

