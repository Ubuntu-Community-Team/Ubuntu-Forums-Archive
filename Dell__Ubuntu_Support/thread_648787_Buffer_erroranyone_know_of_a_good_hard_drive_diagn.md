---
title: "Buffer error/anyone know of a good hard drive diagnostic?"
date: 2007-12-24
forum: Dell  Ubuntu Support
---

### Post by TracyO on 2007-12-24
I've been using Gutsy for about a month and a half, and when I originally installed it, I had the error "Buffer I/0 error on device fdo logical block 0".  I mentioned this when trying to fix another problem, and a more experienced user was concerned that it may mean something is wrong with my hard drive.  Basically, now I have the time to look into it, but I don't know where to find a good diagnostic program.  Or else, does anyone know more about this error?  

I'm using a Dell Inspiron 8200 laptop that is 41/2 years old.  I just need to know what the issue is now as opposed to when I take the computer out of the country a month from now for 10 weeks.

Thanks for any help offered!

---

### Post by natehall on 2007-12-24
This link might help. [http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by woodcarver on 2007-12-26
TracyO, do you the manufacturer of the harddrive? If so go to their website and see if they have a diagnostic tool. Most of them have one that creates a bootable floppy or CD. I use the older version from Maxtor, the new one is XP/Vista only. Do you have a floppy drive in your machine?
If you can't find one, I can zip the one I have and send it to you.

---

### Post by TracyO on 2007-12-27
I went to the Dell website, and from what I can find, they only have diagnostics for Windows.

I looked through that forum that Natehall gave me, and I don't think my problem is a bug.  When I originally installed Ubuntu, it took over a day for it to nuke out Windows, so its my hard drive.  I just don't know how bad it is.

I did install the Smart Data program to check, and my numbers are appropriate for how long I've had Ubuntu.

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   104   104   040    Pre-fail  Offline      -       5964
  3 Spin_Up_Time            0x0007   128   128   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   099   099   000    Old_age   Always       -       1962
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   134   134   040    Pre-fail  Offline      -       30
  9 Power_On_Hours          0x0012   072   072   000    Old_age   Always       -       12635
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1947
191 G-Sense_Error_Rate      0x000a   099   099   000    Old_age   Always       -       131072
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       22
193 Load_Cycle_Count        0x0012   055   055   000    Old_age   Always       -       452920
194 Temperature_Celsius     0x0002   134   134   000    Old_age   Always       -       41 (Lifetime Min/Max 18/68)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0


I am concerned about the type being "old age" so often.  It's no surprise, but I just want to know if there's a way to tell how long I've got.

Thanks for your help!

---

