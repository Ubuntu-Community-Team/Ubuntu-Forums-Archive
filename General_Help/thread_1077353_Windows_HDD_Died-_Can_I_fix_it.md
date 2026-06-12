---
title: "Windows HDD Died- Can I fix it?"
date: 2009-02-22
forum: General Help
---

### Post by KaosKnight on 2009-02-22
My brother has his "gaming" computer that almost never gets turned off; I think the HDD might be dying in it as it's very loud, and Windows either hangs at start-up screen or at the desktop.  I'm currently running Ubuntu through my thumb drive, and was trying to see if I could access or do anything with the HDD; it says the media is not mountable.  Is there anyway I could get in and save some of the data from this drive?  I'm most likely going to ditch the drive and do a clean install of windows, but my family has a few files they'd like to keep.

---

### Post by kmac on 2009-02-22
> **KaosKnight said:**
> My brother has his "gaming" computer that almost never gets turned off; I think the HDD might be dying in it as it's very loud, and Windows either hangs at start-up screen or at the desktop.  I'm currently running Ubuntu through my thumb drive, and was trying to see if I could access or do anything with the HDD; it says the media is not mountable.  Is there anyway I could get in and save some of the data from this drive?  I'm most likely going to ditch the drive and do a clean install of windows, but my family has a few files they'd like to keep.

What error do you get under "details" when you attempt to mount the HD?

---

### Post by KaosKnight on 2009-02-22
When I try a partition check & repair through GParted, I get this:
> GParted 0.3.8

Libparted 1.8.9

Check and repair filesystem (ntfs) on /dev/sda1  00:00:02    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 268414019
size: 268413957 (127.99 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00:02    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 137427943936 bytes (137428 MB)
Current device size: 137427945984 bytes (137428 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 184117 (0x2cf35): missing cluster in $Bitmap
Cluster accounting failed at 184118 (0x2cf36): missing cluster in $Bitmap
Cluster accounting failed at 184119 (0x2cf37): missing cluster in $Bitmap
Cluster accounting failed at 184133 (0x2cf45): missing cluster in $Bitmap
Cluster accounting failed at 184134 (0x2cf46): missing cluster in $Bitmap
Cluster accounting failed at 184135 (0x2cf47): missing cluster in $Bitmap
Cluster accounting failed at 185615 (0x2d50f): missing cluster in $Bitmap
Cluster accounting failed at 191050 (0x2ea4a): extra cluster in $Bitmap
Cluster accounting failed at 228920 (0x37e38): extra cluster in $Bitmap
Cluster accounting failed at 5083094 (0x4d8fd6): missing cluster in $Bitmap
Cluster accounting failed at 5083095 (0x4d8fd7): missing cluster in $Bitmap
Filesystem check failed! Totally 11 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

========================================

I'm trying to chkdsk, but it gets to 100% on step 3 and appears to hang......I'm about to head out to work, but I'll leave the comp running chkdsk; i'll update when I get home tonight.

---

### Post by KaosKnight on 2009-02-23
chkdsk worked succesfully, but comp still freezes at desktop.

---

### Post by KaosKnight on 2009-02-23
bump; I'm posting from the comp right now through my Ubuntu USB, and still can't mount the HDD even after Windows did Chkdsk successfully.  I get a different error now (print screened and uploaded it):

---

### Post by sailthesea on 2009-02-23
You need windows help with one mate!
It sounds like its a goner though, you may be able to dock the HD and rescue some of it, depends where you work really

---

### Post by KaosKnight on 2009-02-24
> **sailthesea said:**
> You need windows help with one mate!
It sounds like its a goner though, you may be able to dock the HD and rescue some of it, depends where you work really

That's just it though; I can't really do anything in Windows.  IF the computer boots up and logs me in, then I have 30 seconds to a minute to do anything before it hangs; nothing is clickable, no keyboard functions.  The mouse will move until I click on something, then it freezes too.

---

### Post by sailthesea on 2009-02-24
You could try wiring your your ubuntu machine to the broken one and trying to access the data thats left in the drive but you'll probably need a null lead as the os is down and an ethernet connection most likely won't play Failing that you could take the HDD out and try installing it in a working windows desktop as an auxiliary drive and try that way but it won't be easy cause it sounds like its pretty well fried
 Good luck!

---

### Post by KaosKnight on 2009-02-24
I currently have 1 running machine in my house; my Ubuntu laptop.  This windows machine was the only other running one in the house, so I don't have another Windows machine to hook it upto.  I booted into Ubuntu from my USB on the Windows machine, which is how I've gotten the info I have.


Dug up some receipts and it looks like I have a 3yr warranty on this, so I'll probably just send it out for repair.  Thanks for the help though guys :)

---

### Post by sailthesea on 2009-02-24
That would be the best thing to do Unless you're a God at DOS The data should be mostly recoverable but I'll bet theres a ton of viruses in there,
which is why I use Ubuntu

---

### Post by halok on 2009-02-24
the error that you are getting is becuase the ntfs volume was not shut down properly, as the attatched pic says.. try the following

> sudo mkdir /media/temp

sudo mount -t ntfs-3g /dev/sda1 /media/temp -o force

hope this helps

---

### Post by Skripka on 2009-02-24
> **KaosKnight said:**
> I currently have 1 running machine in my house; my Ubuntu laptop.  This windows machine was the only other running one in the house, so I don't have another Windows machine to hook it upto.  I booted into Ubuntu from my USB on the Windows machine, which is how I've gotten the info I have.


Dug up some receipts and it looks like I have a 3yr warranty on this, so I'll probably just send it out for repair.  Thanks for the help though guys :)

Be warned, they'll probably nuke your data....

---

### Post by KaosKnight on 2009-02-25
> **halok said:**
> the error that you are getting is becuase the ntfs volume was not shut down properly, as the attatched pic says.. try the following



hope this helps


I'll give that a try tomorrow; I tried running the commands in the pic and few other ways to mount it, but no success.  

> **Skripka said:**
> Be warned, they'll probably nuke your data....

I know, and it's a last resort, but nothing else seems to be working, and since I'm the only one in my family who uses Ubuntu (can't get them to switch for some reason), I'm the only one with a comp in this electronic age :P

---

### Post by KaosKnight on 2009-02-27
Got the HD mounted, ran a check & repair through GParted and the system seems to be fine.  I already backed up most of my important files on another comp and my thumb drive just in case.  Do you guys think I should go ahead and get the drive replaced, or should I just leave it be and see what it does?

---

### Post by ryan.nabinger on 2009-02-27
Check the S.M.A.R.T. params.  IMO, HDs are cheap compared to data recovery ...

---

