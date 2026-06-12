---
title: "How to get the daily desktop iso FAST using rsync for windows"
date: 2007-01-21
forum: Development CD/DVD Image Testing
---

### Post by UBfusion on 2007-01-21
I experimented a bit this Sunday morning and I have found, successfully installed and used a Windows version of cwRsync (Rsync for Windows), unfortunately without a GUI.

This method will allow you to update a previous already downloaded build of the daily iso in no time. The procedure appears long but in fact won't take more than 5 minutes.

1. Put the previous daily iso of feisty in a dedicated dir. In my case it was **g:\feisty**. Best leave the iso filename as is.

2. Go to [**cwRsync** homepage]("http://www.itefix.no/phpws/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=6&MMN_position=150:150") (**[link here]("http://www.itefix.no/phpws/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=6&MMN_position=150:150")**) and download it.

3. Install **cwRsync** to its default location (probably c:\Program Files\cwRsync)

4. You will find in there 2 directories and **cwrsync.cmd**, which is the batch file you will use and that needs some editing, as follows:

[LIST]the line **SET CWRSYNCHOME=C:\Program Files\CWRSYNC** should point at your CWRSYNC installation dir
[/LIST]

[LIST]after the last **REM ** CUSTOMIZE **** line enter the following line:
[/LIST]

```
"c:\Program Files\cwRsync\bin\rsync" -vPz cdimage.ubuntu.com::cdimage/daily-live/current/feisty-desktop-amd64.iso /cygdrive/g/feisty/feisty-desktop-amd64.iso
```

[INDENT]Important notes:

 a) The **" "** in the path to rsync is needed because "Program Files" has a space in it
 
  b) **cdimage.ubuntu.com::** is the equivalent of http:/ and indicates to rsync that it's a remote host

  c) the last part is the destination file to be updated, where in my case **g:\feisty** must be translated to **/cygdrive/g/feisty/** (cygwin's notation of windows **drive:\path**)[/INDENT]

5. Open a command prompt and CD to the cwRsync installed directory (this is just to be able to keep the cwrsync results in your cmd prompt window)

6. Run the batch file ```
cwRsync.cmd
``` and watch what happens :-)

7. Your old iso will be updated to the latest daily version in no time. You can verify it's the correct build by viewing the contents of the .disk directory in the iso.

Just in case, verify it with its respective MD5SUM. The way I do it with Total Commander (my swiss knife in windoze) is to save the MD5SUM from the site as MD5SUM.MD5 in the same dir as the iso, and run it, and see if the checksum is OK.

Updating from 20070120 to 20070121 (yesterday to today) took under a minute :p

This method should also work for kubuntu and edubuntu with the appropriate changes in the filenames above.

Please provide feedback and errors so I can correct and finalise this mini-guide!

---

### Post by tchoklat on 2007-01-22
how do you do this in Ubuntu without windows?

---

### Post by pochu on 2007-01-22
> **tchoklat said:**
> how do you do this in Ubuntu without windows?
Look at this:

[https://help.ubuntu.com/community/RsyncCdImage](https://help.ubuntu.com/community/RsyncCdImage)

---

### Post by tchoklat on 2007-01-23
I have the feisty iso on my desktop and enter into terminal;

tony@tony:~/Desktop$ rsync -avzpPv --stats rsync://cdimage.ubuntu.com/cdimage/ubuntu/daily-live/current/feisty-desktop-i386.iso .
opening tcp connection to cdimage.ubuntu.com port 873
opening connection using --server --sender -vvlogDtprz . cdimage/ubuntu/daily-live/current/feisty-desktop-i386.iso 
receiving file list ... 
rsync: link_stat "/ubuntu/daily-live/current/feisty-desktop-i386.iso" (in cdimage) failed: No such file or directory (2)
0 files to consider

rsync[8144] (receiver) heap statistics:
  arena:         135168   (bytes from sbrk)
  ordblks:            2   (chunks not in use)
  smblks:             0
  hblks:              0   (chunks from mmap)
  hblkhd:             0   (bytes from mmap)
  allmem:        135168   (bytes from sbrk + mmap)
  usmblks:            0
  fsmblks:            0
  uordblks:       54928   (bytes used)
  fordblks:       80240   (bytes free)
  keepcost:       80216   (bytes in releasable chunk)

Number of files: 0
Number of files transferred: 0
Total file size: 0 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 13
Total bytes sent: 4
Total bytes received: 17

sent 4 bytes  received 17 bytes  2.21 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files could not be transferred (code 23) at main.c(1298) [receiver=2.6.8]

I tried thius command;

rsync -vPz rsync://cdimage.ubuntu.com/cdimage/daily-live/current/*i386.iso .

wuith the dot at the end ...:guitar:

---

### Post by garba on 2007-01-29
excellent suggestion ubfusion thanks :)

---

### Post by UBfusion on 2007-01-29
Isn't it a charm? From one day to the next the needed download is 70 - 100 MB maximum, today it was 70 :) 

This is really saving bandwidth! Unfortunately the torrent model does not work with daily builds, noone gets them concurrently with you. Perhaps when Herd3 is released it will make sense (and I'll be seeding too).

---

