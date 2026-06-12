---
title: "How to Locate the Fault Disk?"
date: 2009-04-29
forum: Desktop Environments
---

### Post by huangyingw on 2009-04-29
Hello, my PC sometimes experienced I/O error when using rsync, sometimes just no response, and I have to manually reboot it.
I have 5 hard disks, two patas, three satas to setup a lv using lvm. Thus, I have difficulty at locating the true fault disk.
smartctl tells me sdd is the fault one. For my output of smartctl -l error /dev/sdd > /media/storage/storage/sdd.txt is
```

smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
ATA Error Count: 47 (device log contains only the most recent five errors)
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

Error 47 occurred at disk power-on lifetime: 10462 hours (435 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 5f f8 69 df ec  Error: ICRC, ABRT 95 sectors at LBA = 0x0cdf69f8 = 215968248

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 80 d7 69 df ec 00      00:05:54.059  READ DMA
  c8 00 80 5f 81 df ec 00      00:05:54.055  READ DMA
  c8 00 20 ef 9a df ec 00      00:05:54.053  READ DMA
  c8 00 80 57 69 df ec 00      00:05:54.051  READ DMA
  c8 00 70 67 79 df ec 00      00:05:54.043  READ DMA

Error 46 occurred at disk power-on lifetime: 8515 hours (354 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 6a ee e1 e0  Error: ICRC, ABRT at LBA = 0x00e1ee6a = 14806634

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 6a ee e1 e0 00      20:51:02.448  READ DMA EXT
  25 00 01 a1 04 53 e0 00      20:51:02.436  READ DMA EXT
  25 00 01 2b ee e1 e0 00      20:51:02.436  READ DMA EXT
  25 00 01 00 00 00 e0 00      20:51:02.436  READ DMA EXT
  25 00 01 00 00 00 e0 00      20:51:02.432  READ DMA EXT

Error 45 occurred at disk power-on lifetime: 8515 hours (354 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 6a ee e1 e0  Error: ICRC, ABRT at LBA = 0x00e1ee6a = 14806634

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 6a ee e1 e0 00      20:51:01.213  READ DMA EXT
  25 00 01 a1 04 53 e0 00      20:51:01.213  READ DMA EXT
  25 00 01 2b ee e1 e0 00      20:51:01.213  READ DMA EXT
  25 00 01 00 00 00 e0 00      20:51:01.198  READ DMA EXT
  25 00 01 00 00 00 e0 00      20:51:00.518  READ DMA EXT

Error 44 occurred at disk power-on lifetime: 8515 hours (354 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 6a ee e1 e0  Error: ICRC, ABRT at LBA = 0x00e1ee6a = 14806634

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 6a ee e1 e0 00      20:50:58.832  READ DMA EXT
  25 00 01 a1 04 53 e0 00      20:50:58.183  READ DMA EXT
  25 00 01 2b ee e1 e0 00      20:50:58.168  READ DMA EXT
  25 00 01 00 00 00 e0 00      20:50:58.156  READ DMA EXT
  25 00 01 00 00 00 e0 00      20:51:00.518  READ DMA EXT

Error 43 occurred at disk power-on lifetime: 8515 hours (354 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 6a ee e1 e0  Error: ICRC, ABRT at LBA = 0x00e1ee6a = 14806634

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 6a ee e1 e0 00      20:50:58.832  READ DMA EXT
  25 00 01 a1 04 53 e0 00      20:50:58.183  READ DMA EXT
  25 00 01 2b ee e1 e0 00      20:50:58.168  READ DMA EXT
  25 00 01 00 00 00 e0 00      20:50:58.156  READ DMA EXT
  25 00 01 00 00 00 e0 00      20:50:58.156  READ DMA EXT

```
While , smartctl -H /dev/sdd tells me that sdd is passed.
So, to which should I believe?
My experience tells me that another disk would hang when working for a long time, is there a method to check/confirm this?

---

