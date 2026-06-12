---
title: "system monitor gnome extension"
date: 2020-04-30
forum: Desktop Environments
---

### Post by jgw on 2020-04-30
I have system monitor gnome extension installed on my system.  It has been working fine and is updated.  Now, however, when it monitors disk activity 'disk' I show that I am reading the disk (don't know which one) full on.  At the same time there is no evidence of that from the computer (no disk access light).  So, am I constantly accessing my hard disk or is there something wrong with the extension?

I tried atop, pressed 'd' and got "no disk activity"

greg@movies:~$ iostat

```

Linux 4.15.0-99-generic (movies) 	04/30/2020 	_x86_64_	(4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           9.84   17.71    9.59    0.55    0.00   62.31

Device             tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
loop0             0.00         0.02         0.00       1058          0
loop1             0.03         0.03         0.00       1288          0
loop2             0.00         0.00         0.00        133          0
loop3             0.00         0.02         0.00       1111          0
loop4             0.00         0.01         0.00        348          0
loop5             0.00         0.00         0.00        108          0
loop6             0.00         0.02         0.00       1129          0
loop7             0.00         0.01         0.00        500          0
sda               0.99        76.63       311.13    3604977   14637200
sdb               9.85       452.14       372.65   21270974   17531513
loop8             0.00         0.02         0.00       1112          0
loop9             0.00         0.01         0.00        510          0
loop10            0.00         0.00         0.00        122          0
loop11            0.00         0.01         0.00        328          0
loop12            0.00         0.02         0.00       1144          0
loop13            0.00         0.02         0.00       1036          0
loop14            0.00         0.02         0.00       1099          0
loop15            0.00         0.00         0.00        108          0
loop16            0.00         0.02         0.00       1094          0
loop17            0.39         0.42         0.00      19554          0
loop18            0.00         0.02         0.00       1117          0
loop19            0.00         0.00         0.00         46          0
loop20            0.11         0.12         0.00       5450          0
loop21            0.00         0.01         0.00        328          0
loop22            0.00         0.00         0.00        125          0
loop23            0.00         0.02         0.00       1071          0
loop24            0.01         0.02         0.00        988          0
loop25            0.00         0.02         0.00       1140          0
loop26            0.00         0.02         0.00       1109          0
loop27            0.00         0.01         0.00        334          0
loop28            0.00         0.00         0.00        108          0
loop29            0.00         0.00         0.00         47          0
loop30            0.00         0.00         0.00        118          0
loop31            0.00         0.02         0.00       1064          0
loop32            0.01         0.02         0.00        847          0
loop33            0.00         0.01         0.00        357          0
loop34            0.00         0.01         0.00        328          0
loop35            0.00         0.00         0.00        116          0
loop36            0.00         0.00         0.00          8          0

```

Thoughts?

---

### Post by rbmorse on 2020-04-30
Can you tell us a little about the drives? 

I know that hard drives using SMR (Shingled Magnetic Recording) designs have to do a lot of "housekeeping" when the disk is otherwise idle. My WD Red series don't trigger the disk activity LED when they're gnawing away on themselves.  Both are headed to the dumpster as soon as I find the round tuit to get it done because they weren't advertised as SMR devices and if I would have wanted SMR I would have sought out SMR devices.  OTOH, both perform flawlessly in their assigned roles as internally mounted, first-level user files backup on two different machines. 

I also suspect they're data center pulls sold as "white box OEM" drives.   They're listed as no warranty support available on the WD serial number checker.  Conveniently, the reseller I got them from no longer has a web presence nor land line phone service at the number on the receipt. Shop carefully, kids.  Things are tough out there.

---

