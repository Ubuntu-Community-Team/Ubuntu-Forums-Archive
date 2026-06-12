---
title: "using parted to examine hard disk"
date: 2009-04-20
forum: General Help
---

### Post by ayastona on 2009-04-20
hey when i use the command:

parted (enter)
print  (enter)

i get the following output about my hard disk...

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  247GB  247GB   primary   ext3         boot 
 2      247GB   250GB  3093MB  extended                    
 5      247GB   250GB  3093MB  logical   linux-swap        

how come im getting warnings about my disk space being low??
it says i only have 800kb free and that im using about 20 GB of space..

my hard drive is 250 GB!! what do i do??

---

### Post by cariboo on 2009-04-20
At the prompt type:

```
df -h
```

this will give you an output that is human readable, this is the output I get when I run the command:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             5.5G  3.7G  1.6G  71% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  168K  1.5G   1% /dev
tmpfs                 1.5G  188K  1.5G   1% /dev/shm
lrm                   1.5G  2.7M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb2             108G   59G   43G  58% /home
/dev/sda1             151G  117G   27G  82% /home/storage
```

If you are running out of hard drive space at the prompt type:

```
sudo apt-get clean
```

and just in case

```
sudo apt-get autoremove
```

The above commands will remove archived packages in /var/cache/apt/archives, and remove unneeded dependencies.

Jim

---

### Post by ayastona on 2009-04-20
this is what i get when i type: df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G   22G  194G  10% /
tmpfs                 504M     0  504M   0% /lib/init/rw
varrun                504M  208K  504M   1% /var/run
varlock               504M     0  504M   0% /var/lock
udev                  504M  2.8M  501M   1% /dev
tmpfs                 504M  268K  504M   1% /dev/shm
lrm                   504M  2.0M  502M   1% /lib/modules/2.6.27-11-generic/volatile
```

so why is my system telling me im running out of room?

---

### Post by ayastona on 2009-04-21
check out the info in the image here.. look at the differnt windows and see what the information is telling you...

what the hell is up with my system? its saying i have tons of room and that i dont have tons of room at the same time!
EDIT: **** that image is too small on the site..

basically on the left, dolphin in root is telling  me that i have over 140 GB free on the filesystem..

on the right the disk usage analyzer is saying that i only have 20 some GB TOTAL on my "/" folder... im confused!

---

### Post by zman58 on 2009-04-21
How does your system tell you that it is running out of hard drive space? What happens and when does it happen?

---

### Post by ayastona on 2009-04-21
it happened in a couple of different places..

one time i opened a sound file in audacity (like an hour ago) and it was like "disk space is dangerously low" and before that i noticed it cause i was trying to download a file via Ktorrent.. the file was 1.6 GB and ktorrent wouldnt download it cause it said i only had 7.6 mb free... i was like wtf! then i checked and my hard disk apparantly had only 7.6 mb free as was suggested by Ktorrent... then i did a bunch of crap and checked the free disk space again (im checking the free disk space by checking the "properties" of the "/" folder...).. and this time when i checked it was 800kb free! so then i restarted and ****... and then when i check the "properties" of "/" folder now its saying i have 194 GB free.. so it seems **** is working but when i go to the "disk usage analyzer" it says that the god damn system is only 22 GB TOTAL... and that i have like no room to put my balls out to cool... okay not balls out to cool but im frustrated and my balls are getting sweaty tryna figure this out! WTF linux!

---

### Post by zman58 on 2009-04-21
My first suspicion would be hardware. Power down the system and make sure the drive connections are fully plugged in. Pull them and reconnect. You could have an intermittent connection on a conductor and the drive is limping along. I have seen this type of behavior before on IDE hard drives. 

Another possibility is that the hard drive is failing. How old is it? Has it been abused, such as dropped? Just some things to think about.

If that does not work, then you might check it using smartmontools.
[http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html](http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html)

---

### Post by zman58 on 2009-04-21
zadmin@zpresario2:/home/kzahorec$ sudo smartctl -i /dev/sda
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     ST3250410AS
Serial Number:    6RYFLQKH
Firmware Version: 4.AAA
User Capacity:    250,059,350,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Apr 21 00:35:48 2009 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

---

### Post by zman58 on 2009-04-21
Another possibility could be temperature. Is you drive running hot? Here is example output from smartctl on my system:

[INDENT][INDENT]zadmin@zpresario2:/home/kzahorec$ sudo smartctl -d ata -H /dev/sda
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

zadmin@zpresario2:/home/kzahorec$ sudo smartctl -d ata -a /dev/sda
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     ST3250410AS
Serial Number:    6RYFLQKH
Firmware Version: 4.AAA
User Capacity:    250,059,350,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Apr 21 00:41:15 2009 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  64) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       53
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       699064
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       201
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       53
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   071   069   045    Old_age   Always       -       521273373
194 Temperature_Celsius     0x0022   029   031   000    Old_age   Always       -       29 (Lifetime Min/Max 0/18)
195 Hardware_ECC_Recovered  0x001a   070   058   000    Old_age   Always       -       114337074
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1

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

zadmin@zpresario2:/home/kzahorec$ 
[/INDENT][/INDENT]

---

