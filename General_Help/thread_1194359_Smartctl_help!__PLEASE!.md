---
title: "Smartctl help!  PLEASE!"
date: 2009-06-22
forum: General Help
---

### Post by josephellengar on 2009-06-22
My smartctl is scaring me.  Does pre-fail mean failure is imminent (ie we are going to fail very soon) or far off (ie we are very pre-pre fail?)  I've got old age and prefail for all of my variables. See below:

```



SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       24
  3 Spin_Up_Time            0x0027   160   159   021    Pre-fail  Always       -       1000
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1661
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002f   100   253   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1438
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1611
187 Reported_Uncorrect      0x0032   100   082   000    Old_age   Always       -       18
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   058   037   040    Old_age   Always   In_the_past 42
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       605
193 Load_Cycle_Count        0x0032   178   178   000    Old_age   Always       -       66108
194 Temperature_Celsius     0x0022   101   080   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 18 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 18 occurred at disk power-on lifetime: 87 hours (3 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 f0 48 3b e6  Error: AMNF at LBA = 0x063b48f0 = 104548592

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f0 48 3b 06 00      00:47:47.134  READ DMA
  ec 00 00 00 00 00 00 00      00:47:47.125  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 00      00:47:47.114  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:47:47.108  IDENTIFY DEVICE
  c8 00 08 f0 48 3b 06 00      00:47:43.245  READ DMA

Error 17 occurred at disk power-on lifetime: 87 hours (3 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 f0 48 3b e6  Error: AMNF at LBA = 0x063b48f0 = 104548592

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f0 48 3b 06 00      00:47:43.245  READ DMA
  ec 00 00 00 00 00 00 00      00:47:43.232  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 00      00:47:43.221  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:47:43.214  IDENTIFY DEVICE
  c8 00 08 f0 48 3b 06 00      00:47:39.360  READ DMA

Error 16 occurred at disk power-on lifetime: 87 hours (3 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 f0 48 3b e6  Error: AMNF at LBA = 0x063b48f0 = 104548592

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f0 48 3b 06 00      00:47:39.360  READ DMA
  ec 00 00 00 00 00 00 00      00:47:39.347  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 00      00:47:39.336  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:47:39.330  IDENTIFY DEVICE
  c8 00 08 f0 48 3b 06 00      00:47:35.475  READ DMA

Error 15 occurred at disk power-on lifetime: 87 hours (3 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 f0 48 3b e6  Error: AMNF at LBA = 0x063b48f0 = 104548592

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f0 48 3b 06 00      00:47:35.475  READ DMA
  ec 00 00 00 00 00 00 00      00:47:35.462  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 00      00:47:35.451  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:47:35.446  IDENTIFY DEVICE
  c8 00 08 f0 48 3b 06 00      00:47:31.586  READ DMA

Error 14 occurred at disk power-on lifetime: 87 hours (3 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 f0 48 3b e6  Error: AMNF at LBA = 0x063b48f0 = 104548592

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f0 48 3b 06 00      00:47:31.586  READ DMA
  ec 00 00 00 00 00 00 00      00:47:31.573  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 00      00:47:31.562  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:47:31.552  IDENTIFY DEVICE
  c8 00 08 f0 48 3b 06 00      00:47:27.677  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Aborted by host               90%         1         -
# 2  Short offline       Completed without error       00%         1         -

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

---

