---
title: "Fix bad sectors"
date: 2008-12-07
forum: General Help
---

### Post by epqr on 2008-12-07
i was going to reinstall my windows today. HOwever i ran into some trouble, and i found out that my Harddrive have some bad sectors. I was therefore unable to properly install windows, some files where not copied ot the HD. I was however able to install ubuntu (which is the most important;)).

So i am wondering if there is some way of fix the bad sectors with linux?

---

### Post by theozzlives on 2008-12-07
fsck

---

### Post by mk1w86 on 2008-12-07
You can run diagnostic tools for your drive which can sometimes mark bad sectors as unusable.  The diagnostics can usually be downloaded from the the manufacturers website of your hard drive.

However if a hard drive has bad sectors I would recommend replacing it because you are at risk of losing data.

---

### Post by epqr on 2008-12-07
> **theozzlives said:**
> fsck

i get:

```
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=f5c9bc83-057c-4880-9d97-00ae94c25279'

```

> You can run diagnostic tools for your drive which can sometimes mark bad sectors as unusable. The diagnostics can usually be downloaded from the the manufacturers website of your hard drive.

However if a hard drive has bad sectors I would recommend replacing it because you are at risk of losing data.

And how would i do that?

^ sorry misunderstood. But i doubt i will find that kind of software for linux? how can i find out which type of HD i have? (without opening the computer)

---

### Post by mk1w86 on 2008-12-07
The diagnostics would usually run off a DOS based boot disk.
You can sometimes work out the brand of drive by looking in the bios, if not Drive Fitness test diagnostic is a good place to start although I am not sure it will resolve the bad sectors because it will be a generic test and not drive model specific unless you have an IBM or Hitachi drive.

Drive Fitness Test:
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

Download link for Drive Fitness Test ISO:
[http://www.hitachigst.com/hdd/support/downloads/dft32_v414_b00.iso](http://www.hitachigst.com/hdd/support/downloads/dft32_v414_b00.iso)

You could also try Ultimate Boot CD which has many diagnostic tools for various drives:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by mk1w86 on 2008-12-07
To find your drive model under linux run:

```
sudo hdparm -I /dev/sda
```

where /dev/sda is the device your hard drive is.

---

### Post by caljohnsmith on 2008-12-07
If you want, you can run the HDD diagnostic test from Ubuntu by doing the following:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And then post the results of those two files so we can see what your HDD's health is like at this point. :)

---

### Post by epqr on 2008-12-07
> **mk1w86 said:**
> To find your drive model under linux run:

```
sudo hdparm -I /dev/sda
```

where /dev/sda is the device your hard drive is.

I get this

```
/dev/sda:

ATA device, with non-removable media
	Model Number:       ST9120821AS                             
	Serial Number:      5PL42H5A
	Firmware Revision:  7.24    
Standards:
	Supported: 7 6 5 4 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  234441648
	LBA48  user addressable sectors:  234441648
	device size with M = 1024*1024:      114473 MBytes
	device size with M = 1000*1000:      120034 MBytes (120 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 128
	Recommended acoustic management value: 254, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Phy event counters
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	66min for SECURITY ERASE UNIT. 66min for ENHANCED SECURITY ERASE UNIT.
Checksum: correct
jonesu1@jonesu1-laptop:~$ sudo hdparm -I /dev/sda1
[sudo] password for jonesu1: 

/dev/sda1:

ATA device, with non-removable media
	Model Number:       ST9120821AS                             
	Serial Number:      5PL42H5A
	Firmware Revision:  7.24    
Standards:
	Supported: 7 6 5 4 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  234441648
	LBA48  user addressable sectors:  234441648
	device size with M = 1024*1024:      114473 MBytes
	device size with M = 1000*1000:      120034 MBytes (120 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 128
	Recommended acoustic management value: 254, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Phy event counters
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	66min for SECURITY ERASE UNIT. 66min for ENHANCED SECURITY ERASE UNIT.

```

i don't see a manufacturer there :P

---

### Post by mk1w86 on 2008-12-07
ST9120821AS suggests the drive is a Seagate.

---

### Post by epqr on 2008-12-07
> **caljohnsmith said:**
> If you want, you can run the HDD diagnostic test from Ubuntu by doing the following:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And then post the results of those two files so we can see what your HDD's health is like at this point. :)

```
Self-test execution status:   
 (  73)	The previous self-test completed having
	a test element that failed and the test

```

I get that and it doesn't change (if i do it again after a while). Does the test still run or is something wrong ?

---

### Post by caljohnsmith on 2008-12-07
How about first posting the output of:
```
sudo smartctl -a /dev/sda
```

---

### Post by epqr on 2008-12-07
```
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.2 series
Device Model:     ST9120821AS
Serial Number:    5PL42H5A
Firmware Version: 7.24
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Dec  7 21:39:45 2008 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (  73)	The previous self-test completed having
					a test element that failed and the test
					element that failed is not known.
Total time to complete Offline 
data collection: 		 ( 426) seconds.
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
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  68) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0002   095   094   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   098   098   020    Pre-fail  Always       -       2373
  5 Reallocated_Sector_Ct   0x0033   001   001   036    Pre-fail  Always   FAILING_NOW 17218
  7 Seek_Error_Rate         0x000f   062   060   030    Pre-fail  Always       -       580054965077
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4865
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   098   098   020    Pre-fail  Always       -       2752
187 Unknown_Attribute       0x0032   001   001   000    Old_age   Always       -       65535
189 Unknown_Attribute       0x003a   001   001   000    Old_age   Always       -       156
190 Temperature_Celsius     0x0022   060   035   045    Old_age   Always   In_the_past 4179676561448
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1421
193 Load_Cycle_Count        0x0032   036   036   000    Old_age   Always       -       128243
194 Temperature_Celsius     0x0022   040   065   000    Old_age   Always       -       40 (Lifetime Min/Max 0/8)
195 Hardware_ECC_Recovered  0x001a   065   048   000    Old_age   Always       -       109293213
197 Current_Pending_Sector  0x0012   052   052   000    Old_age   Always       -       985
198 Offline_Uncorrectable   0x0010   052   052   000    Old_age   Offline      -       985
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 23335 (device log contains only the most recent five errors)
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

Error 23335 occurred at disk power-on lifetime: 4859 hours (202 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 1b 73 48 ec  Error: UNC at LBA = 0x0c48731b = 206074651

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 1b 73 48 ec 00      00:06:41.449  READ DMA
  ec 00 00 00 00 00 a0 00      00:06:41.438  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:06:41.430  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:06:39.127  IDENTIFY DEVICE
  c8 00 08 1b 73 48 ec 00      00:06:39.121  READ DMA

Error 23334 occurred at disk power-on lifetime: 4859 hours (202 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 1b 73 48 ec  Error: UNC at LBA = 0x0c48731b = 206074651

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 1b 73 48 ec 00      00:06:32.151  READ DMA
  ec 00 00 00 00 00 a0 00      00:06:32.136  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:06:32.115  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:06:39.127  IDENTIFY DEVICE
  c8 00 08 1b 73 48 ec 00      00:06:39.121  READ DMA

Error 23333 occurred at disk power-on lifetime: 4859 hours (202 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 1b 73 48 ec  Error: UNC at LBA = 0x0c48731b = 206074651

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 1b 73 48 ec 00      00:06:32.151  READ DMA
  ec 00 00 00 00 00 a0 00      00:06:32.136  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:06:32.115  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:06:32.110  IDENTIFY DEVICE
  c8 00 08 1b 73 48 ec 00      00:06:29.652  READ DMA

Error 23332 occurred at disk power-on lifetime: 4859 hours (202 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 1b 73 48 ec  Error: UNC at LBA = 0x0c48731b = 206074651

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 1b 73 48 ec 00      00:06:32.151  READ DMA
  ec 00 00 00 00 00 a0 00      00:06:32.136  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:06:32.115  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:06:32.110  IDENTIFY DEVICE
  c8 00 08 1b 73 48 ec 00      00:06:29.652  READ DMA

Error 23331 occurred at disk power-on lifetime: 4859 hours (202 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 1b 73 48 ec  Error: UNC at LBA = 0x0c48731b = 206074651

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 1b 73 48 ec 00      00:06:32.151  READ DMA
  ec 00 00 00 00 00 a0 00      00:06:32.136  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:06:32.115  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:06:32.110  IDENTIFY DEVICE
  c8 00 08 1b 73 48 ec 00      00:06:29.652  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: unknown failure    90%      4865         68334095
# 2  Extended offline    Completed: unknown failure    90%      4865         56246948
# 3  Short offline       Completed: unknown failure    90%      4863         104458408
# 4  Short offline       Completed: unknown failure    90%      4863         213701665
# 5  Short offline       Completed: unknown failure    90%      4863         45990864
# 6  Short offline       Completed: unknown failure    90%      4863         176763354
# 7  Short offline       Completed: unknown failure    90%      4863         62438542
# 8  Short offline       Completed: unknown failure    90%      4863         153926940

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

Also the windows partion can no lomnger be mounted. I think this is because it didn't exit windows (the one i cant boot into) properly.

Edit: That doesnt look good :-|

---

### Post by caljohnsmith on 2008-12-07
> **epqr said:**
> ```

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: [COLOR="Red"]FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.[/COLOR]
See vendor-specific Attribute list for failed Attributes.

SMART Error Log Version: 1
[COLOR="Red"]ATA Error Count: 23335[/COLOR] (device log contains only the most recent five errors)

```

Also the windows partion can no lomnger be mounted. I think this is because it didn't exit windows (the one i cant boot into) properly.
Based on the results above, I think your best bet is to recover whatever data you can from the drive and scrap the drive. The results show over 23,000 errors, so it looks like the HDD is on its last legs.

---

### Post by epqr on 2008-12-07
> **caljohnsmith said:**
> Based on the results above, I think your best bet is to recover whatever data you can from the drive and scrap the drive. The results show over 23,000 errors, so it looks like the HDD is on its last legs.

Wow..  Now how did this happen?

Well.. i have no data to backup, since i already wiped the disk when i tried to reinstall vista. I'll try to take it back to my where i bought it and get the HD replaced..

Thanks for all the help


Edit: one more question. Is there any harm for the rest of the computer to leave it in there?

---

### Post by caljohnsmith on 2008-12-07
> **epqr said:**
> Wow..  Now how did this happen?

Well.. i have no data to backup, since i already wiped the disk when i tried to reinstall vista. I'll try to take it back to my where i bought it and get the HD replaced..

Thanks for all the help
Glad I could help out, but it's too bad that the HDD seems to be in such bad shape; hopefully the place where you bought it will replace it without giving you any hassle. Cheers and good luck. :)

EDIT: I think there is very little chance that the HDD would harm the computer by leaving it in, although it could be remotely possible if the electronics malfunctioned; that doesn't look like it is your case though since the software in Ubuntu could at least talk to the HDD OK.

---

### Post by epqr on 2008-12-07
Could you try to answear this to?:) edited a little too late:p

> one more question. Is there any harm for the rest of the computer to leave it in there?Again thank you very much.

EDIT: Nevermind :P

---

### Post by sysghost on 2011-12-30
I know the thread is a bit old, but I'd like to add a comment, as I believe this thread still can prove useful.
What I want to add, is a warning, and an advice.
Once a drive has given indications it will fail soon, one should always save the important data.

But I've seen, even if people do save their data, they tend to use their failing drives until their drives finally gives up.
Sure, one can use a "soon to fail" drive with non-essential data, such as games, programs and other stuff that can be easily replaced/reinstalled.

...but...



**Warning follows: **
The operating system might not behave well when a drive fails. For instance, I had a failing drive with my Windows computer. D:
I was storing games on it. I was thinking: 
-"Heh, what the heck, if it fails I'll just get a new drive and reinstall my games".



**Lesson learned:**
One day, all of a sudden, the D: drive failed and started to click loudly. 
Windows froze. Only a hard reset could bring it back to life.
Soon I learned some of my data on my non-failing C: drive went corrupt in the process.

I lost data on a fresh, well working drive, just because the operating system couldn't handle the D: drive failure in a proper way.



**My suggestion follows:**
If one are to use a "soon to fail" drive for as long as it lives, use it with an operating system that can handle drive failures in a proper way. 
And preferably on it's on ATA-controller, as the failing drive might "stuff up" the whole controller once it fails. 
It would seem the ATA protocol doesn't handle failing drives very well.

---

### Post by oldos2er on 2011-12-30
Closed, necromancy.

---

