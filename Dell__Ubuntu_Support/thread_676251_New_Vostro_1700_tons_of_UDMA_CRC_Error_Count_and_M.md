---
title: "New Vostro 1700 tons of UDMA_CRC_Error_Count and Multi_Zone_Error_Make"
date: 2008-01-23
forum: Dell  Ubuntu Support
---

### Post by joeybutterface on 2008-01-23
UDMA_CRC_Error_Count RAW_VALUE = 263010
Multi_Zone_Error_Make = 680513

These errors are increasing every few seconds. I've only had the laptop for a day and hardly used it yet. Should I be worried about these? The expected raw value would be 0 as far as I know.

I'm using:
sudo smartctl - A /dev/sda

I was only using this to apply the Load_Cycle_Count flaw in Ubuntu that kills hard drives.

Should I call Dell?

---

### Post by joeybutterface on 2008-01-23
Here's the full diagnostic report:

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 128
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1724
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       1065
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       10
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       2
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       280
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       38 (Lifetime Min/Max 12/45)
199 UDMA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       263017
200 Multi_Zone_Error_Rate   0x0032   100   100   000    Old_age   Always       -       680568
240 Head_Flying_Hours       0x0032   100   100   000    Old_age   Always       -       819
241 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       93618289
242 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       80739270

---

