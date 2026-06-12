---
title: "Restoring from multi-DVD backup; Need to ignore DVD errors"
date: 2008-12-31
forum: General Help
---

### Post by MaxIBoy on 2008-12-31
I used hubackup to back up my files onto DVDs before sending my laptop to tech support. Burning a DVD of more than 2 gigs wasn't working for me, and I didn't have enough time to figure out how to fix it, so I used tar to split all the 4 gig .dar files it generated so I could burn them.

Now I need to restore my files. 
[LIST=1]
[*]One of the DVDs turned out to be a total coaster. It was "part 1" of one of the files I split up. Is there any way to fudge a header or something so I can at least recover my files from part 2?
[*]Another DVD has a scratch on it, such that it doesn't get farther than 729 Mb. How can I ignore that scratch? I don't care if some files get corrupted, I just want as much data off that CD as I can get!
[/LIST]

Thank you very much for your time.

---

### Post by dcstar on 2008-12-31
> **MaxIBoy said:**
> I used hubackup to back up my files onto DVDs before sending my laptop to tech support. Burning a DVD of more than 2 gigs wasn't working for me, and I didn't have enough time to figure out how to fix it, so I used tar to split all the 4 gig .dar files it generated so I could burn them.

Now I need to restore my files. 
[LIST=1]
[*]One of the DVDs turned out to be a total coaster. It was "part 1" of one of the files I split up. Is there any way to fudge a header or something so I can at least recover my files from part 2?
[*]Another DVD has a scratch on it, such that it doesn't get farther than 729 Mb. How can I ignore that scratch? I don't care if some files get corrupted, I just want as much data off that CD as I can get!
[/LIST]

Thank you very much for your time.

```
man dd
``` Use a small blocksize and look for the "noerror" option.

---

### Post by MaxIBoy on 2009-01-01
dd can do that?

All right, thanks, that's one problem solved!

---

### Post by MaxIBoy on 2009-01-01
Actually, it doesn't work. dd seems to be re-trying the same bad spot. Here's how I called it:
```
 dd conv=noerror if='/media/cdrom0/archive_8_1.tar' of='/home/maxtothemax/.hubackup-data/archive_8_1.tar' bs=1 
```

This is a SAMPLE of what I get once it reaches a certain point (it adds an extra error message periodically, and I let it sit there doing that for hours. It had gotten really, really long by the time I gave up hope on it.) I find it odd that dd lists 764 MB (that number did not change across any of the error messages, i.e. it wasn't going up with time,) whereas it recovered 729.1 MB of data.
```
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10081.7 s, 75.8 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10087.7 s, 75.8 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10093.7 s, 75.7 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10099.7 s, 75.7 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10105.7 s, 75.6 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10111.7 s, 75.6 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10117.7 s, 75.6 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10123.7 s, 75.5 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10129.7 s, 75.5 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10135.7 s, 75.4 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10141.7 s, 75.4 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10147.7 s, 75.3 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10153.7 s, 75.3 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10159.7 s, 75.2 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10165.7 s, 75.2 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10171.7 s, 75.2 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10177.7 s, 75.1 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10183.7 s, 75.1 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10189.7 s, 75.0 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10195.7 s, 75.0 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10201.7 s, 74.9 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10207.7 s, 74.9 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10213.7 s, 74.8 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10219.7 s, 74.8 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10225.7 s, 74.8 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10231.7 s, 74.7 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10237.7 s, 74.7 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10243.7 s, 74.6 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10249.7 s, 74.6 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10255.7 s, 74.5 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10261.7 s, 74.5 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10267.7 s, 74.5 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10273.7 s, 74.4 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10279.7 s, 74.4 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10285.7 s, 74.3 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10291.7 s, 74.3 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10297.7 s, 74.2 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10303.7 s, 74.2 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10309.7 s, 74.2 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10315.7 s, 74.1 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10321.7 s, 74.1 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10327.7 s, 74.0 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10333.7 s, 74.0 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10339.7 s, 73.9 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10345.7 s, 73.9 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10351.7 s, 73.9 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10357.7 s, 73.8 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10363.7 s, 73.8 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10369.7 s, 73.7 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10375.7 s, 73.7 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10381.7 s, 73.6 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10387.7 s, 73.6 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10393.7 s, 73.6 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10399.7 s, 73.5 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10405.7 s, 73.5 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10411.7 s, 73.4 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10417.7 s, 73.4 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10423.7 s, 73.3 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10429.7 s, 73.3 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10435.7 s, 73.3 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10441.7 s, 73.2 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10447.7 s, 73.2 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10453.7 s, 73.1 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10459.7 s, 73.1 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10465.7 s, 73.0 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10471.7 s, 73.0 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10477.7 s, 73.0 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10483.7 s, 72.9 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10489.7 s, 72.9 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10495.7 s, 72.8 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10501.7 s, 72.8 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10507.7 s, 72.8 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10513.7 s, 72.7 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10519.7 s, 72.7 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10525.7 s, 72.6 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10531.7 s, 72.6 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10537.7 s, 72.5 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10543.7 s, 72.5 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10549.7 s, 72.5 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10555.7 s, 72.4 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10561.7 s, 72.4 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10567.7 s, 72.3 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10573.7 s, 72.3 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10579.7 s, 72.3 kB/s
dd: reading `/media/cdrom0/archive_8_1.tar': Input/output error
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10585.7 s, 72.2 kB/s
764477440+0 records in
764477440+0 records out
764477440 bytes (764 MB) copied, 10585.7 s, 72.2 kB/s
```

---

