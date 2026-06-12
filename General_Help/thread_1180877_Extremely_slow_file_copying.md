---
title: "Extremely slow file copying"
date: 2009-06-07
forum: General Help
---

### Post by bayger on 2009-06-07
I use Ubuntu 9.04 with 3 physical disks. The primary disk is 160GB old Barracuda. I installed the system on it and am using it as a boot drive. System boots pretty fast. The two other disks are 500GB newer seagates used in RAID mirror via mdadm. 

/dev/sda 160GB - boot
/dev/sdb 500GB - in RAID
/dev/sdc 500GB - in RAID

I have a very strange behaviour of my main filesystem (the one on /dev/sda). When I am trying to copy larger files (lets say 1GB or more) from this partition to the other drive the operation is extremely slow (copying to /dev/null is also slow). Sometimes it is 10MB/s, sometimes 4MB/s or even 2MB/s. I am a bit confused, because this drive should read files with speed around 50-60MB/s.

I have tested my /dev/sda drive with hdparm tool. The result is:

```

/dev/sda:
 Timing buffered disk reads:  204 MB in  3.03 seconds =  67.36 MB/sec

```

I also monitored the IO of disk drive using iostat. The sample output is below (gathered during slow-copying):

```

Linux 2.6.28-11-generic (galactica) 	06/03/2009 	_x86_64_	(4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.36    0.02    1.07    7.57    0.00   88.12

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda             134.20    10.59   96.71    1.56  7390.50    97.22    76.20     4.33   44.08   5.08  49.96

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.72    0.00    2.16   18.99    0.00   78.61

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               3.00     0.00  162.00    0.00  5448.00     0.00    33.63    12.14   73.04   6.17 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.25    0.00    1.23   18.23    0.00   80.54

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               8.00     0.00  202.00    0.00  6920.00     0.00    34.26    11.10   55.78   4.95 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.74    0.00    0.74   17.24    0.00   81.28

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               6.00     0.00  206.00    0.00  8808.00     0.00    42.76    10.21   50.41   4.85 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.74    0.00    0.50   16.34    0.00   82.43

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               2.00     0.00  171.00    0.00  5384.00     0.00    31.49    12.10   71.37   5.85 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.74    0.00    0.74   16.95    0.00   81.57

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               3.00     0.00  191.00    0.00  7112.00     0.00    37.24    10.03   52.15   5.24 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.73    0.00    0.24   20.10    0.00   78.93

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               1.00     0.00  181.00    0.00  7008.00     0.00    38.72    11.00   60.07   5.52 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.49    0.00    0.74   19.01    0.00   79.75

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               1.00     0.00  195.00    0.00  8232.00     0.00    42.22    10.14   51.88   5.13 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.97    0.00    2.68   16.30    0.00   80.54

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              34.00     0.00  188.00    0.00  9768.00     0.00    51.96    11.53   59.26   5.32 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.53    0.00    1.06   19.41    0.00   78.99

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               2.00     0.00  162.00    0.00  5016.00     0.00    30.96    12.42   77.68   6.17 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.90    0.00    0.67   17.49    0.00   80.94

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               4.00     0.00  199.00    0.00  7480.00     0.00    37.59    10.54   52.08   5.03 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.74    0.00    0.50   16.63    0.00   82.13

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              14.00     0.00  168.00    0.00  6880.00     0.00    40.95     9.93   61.36   5.93  99.60

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.25    0.00    1.23   14.95    0.00   83.58

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              19.00     0.00  193.00    0.00 13584.00     0.00    70.38     9.85   51.40   5.18 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.50    0.00    0.25   18.30    0.00   80.95

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               2.00     0.00  176.00    0.00  5848.00     0.00    33.23    12.98   74.98   5.68 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.49    0.00    0.49   15.82    0.00   83.21

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              33.00     0.00  182.00    0.00 13728.00     0.00    75.43     9.24   50.57   5.49 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.25    0.00    1.00   20.30    0.00   78.45

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               5.00     0.00  155.00    0.00  8328.00     0.00    53.73    10.52   65.29   6.45 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.48    0.00    0.48   16.75    0.00   82.30

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               3.00     0.00  168.00    0.00  7464.00     0.00    44.43    10.31   60.50   5.95 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.25    0.00    0.99   16.34    0.00   82.43

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              16.00     0.00  175.00    0.00  9856.00     0.00    56.32    10.04   58.79   5.71 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.74    0.00    0.49   17.65    0.00   81.13

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              15.00     0.00  147.00    0.00  5424.00     0.00    36.90    10.15   68.79   6.80 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.50    0.00    0.50   19.50    0.00   79.50

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               3.00     0.00  157.00    0.00  6280.00     0.00    40.00    10.01   65.10   6.37 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           2.02    0.00    0.51   17.68    0.00   79.80

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     0.00  203.00    0.00  6016.00     0.00    29.64    13.64   65.40   4.93 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.23    0.00    0.47   17.14    0.00   82.16

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               4.00     0.00  187.00    0.00  8008.00     0.00    42.82     9.44   51.34   5.37 100.40

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.52    0.00    0.79   17.59    0.00   81.10

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               3.00     0.00  185.00    0.00 10288.00     0.00    55.61     9.34   50.01   5.41 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.23    0.00    0.70   25.93    0.00   73.13

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               9.00     9.00  179.00    5.00  6456.00   112.00    35.70    11.50   63.35   5.43 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.49    0.00    0.74   16.05    0.00   82.96

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              19.00     0.00  185.00    0.00  9536.00     0.00    51.55     8.65   48.67   5.41 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.75    0.00    1.25   20.00    0.00   78.00

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              17.00     0.00  183.00    0.00 13696.00     0.00    74.84     8.05   43.63   5.46 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.49    0.00    0.73   18.25    0.00   80.54

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              16.00     0.00  161.00    0.00  5968.00     0.00    37.07    10.94   65.59   6.21 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.24    0.00    0.49   13.63    0.00   85.64

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              21.00     0.00  183.00    0.00 11552.00     0.00    63.13     9.18   50.19   5.46 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.80    0.00    0.53   18.35    0.00   80.32

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              15.00     0.00  212.00    0.00  9616.00     0.00    45.36     9.32   44.96   4.72 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.23    0.00    0.91   15.95    0.00   82.92

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               6.00     0.00  197.00    0.00  9800.00     0.00    49.75     9.65   48.02   5.08 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.24    0.00    1.45   18.55    0.00   80.00

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              16.00     0.00  180.00    0.00  8032.00     0.00    44.62    11.62   60.40   5.56 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.48    0.00    1.45   16.67    0.00   81.88

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               2.00     0.00  161.00    0.00  6296.00     0.00    39.11    11.37   77.81   6.21 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.49    0.00    0.49   18.02    0.00   80.99

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              38.00     0.00  190.00    0.00 13816.00     0.00    72.72     8.10   42.11   5.26 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.25    0.00    0.75   15.92    0.00   83.08

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              23.00     0.00  178.00    0.00 11424.00     0.00    64.18     7.32   41.78   5.62 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.25    0.00    1.48   18.02    0.00   80.49

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               5.00     0.00  198.00    0.00 10128.00     0.00    51.15     9.56   45.86   5.05 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.49    0.00    0.99   18.02    0.00   80.74

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     0.00  182.00    0.00  4944.00     0.00    27.16    14.58   73.98   5.49 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.69    0.00    2.65   19.52    0.00   76.14

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               5.00     0.00  150.00    0.00  4496.00     0.00    29.97    12.48   86.72   6.67 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.90    0.00    3.81   18.81    0.00   75.48

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              16.00     0.00  164.00    0.00 10832.00     0.00    66.05     9.51   58.76   6.10 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           2.61    0.00    3.32   20.14    0.00   73.93

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               4.00     0.00  178.00    0.00  7200.00     0.00    40.45    10.97   65.01   5.62 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.74    0.00    0.49   17.78    0.00   80.99

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               2.00     0.00  157.00    0.00  6352.00     0.00    40.46    11.16   72.03   6.37 100.00

```

I also tried to convert /dev/sda from ext3 to ext4, but it didn't help. fsck tool doesn't signal any problems on this drive nor the smartmontools.

Any thoughts???

---

### Post by fjgaude on 2009-06-07
What kind of raid is the sdb and sdc on? How was the array formatted?

---

### Post by bayger on 2009-06-07
> **fjgaude said:**
> What kind of raid is the sdb and sdc on? How was the array formatted?

It was createdy by:

```

mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sd[bc]

```

It contains only one ext4 partition. I am not sure that my issue is related to the RAID itself. Maybe, but probably not directly, bacause copying the file to /dev/null is also slow. What's even more interesting CPU is almost idle during file transfer.

---

### Post by lavinog on 2009-06-07
Might not be related, but I saw you were using the seagate 500g drives.
Find out what firmware your 500g seagates are using.
SD15 has a major bug that will prevent you from using your drives after a couple of months.
There was another firmware (I think the one prior to SD15) that has been reported to affect performance.
You can find the firmware version by using
```

sudo hdparm -i /dev/sdb

```
change sdb to sdc for your other drive (I don't know if this works differently for raid setups though)
You can also read it off the label if you never changed the firmware.

The drives affected are 7200.11 Baracuda drives made sometime before feb 09.
I got mine jun08 and it failed jan09. I was able to recover it by following this guide: [http://www.msfn.org/board/index.php?showtopic=128807](http://www.msfn.org/board/index.php?showtopic=128807)
It is not an easy task.  Also I understand that seagate is offering free data recovery to users with this type drive.

---

### Post by lavinog on 2009-06-07
Here is a link from seagate:[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931)

Note they mention if the drives are in a raid array, then you might not be able to recover them.

---

### Post by bayger on 2009-06-07
> **lavinog said:**
> 
The drives affected are 7200.11 Baracuda drives made sometime before feb 09.
I got mine jun08 and it failed jan09. I was able to recover it by following this guide: [http://www.msfn.org/board/index.php?showtopic=128807](http://www.msfn.org/board/index.php?showtopic=128807)
It is not an easy task.  Also I understand that seagate is offering free data recovery to users with this type drive.

Thanks for this info. I have two 7200.11 500GB drives, but fortunately with SD1A firmware. Affected firmwares: [http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951) (you were faster ;))

**UPDATE:**
Copying a large file (large ISO 4.4GB) to RAID and back to /dev/sda solved the problem. Transfer rate is now 45MB/s from /dev/sda. This is really weird.

---

