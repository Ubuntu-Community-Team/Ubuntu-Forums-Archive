---
title: "Violation game integrity 20004"
date: 2007-11-10
forum: Gaming &amp; Leisure
---

### Post by Molatove on 2007-11-10
I have installed enemy territory on ubuntu 7.10 the game went well till i loaded the 2.60b patch. Now i get kicked by punkbuster as a hack threat
 (violation game integrity 20004)  i have updated punkbuster 
via the drop down console  still get the problem. Has anybody seen this
before, the game works  on windows xp ,would like it to run on linux.
Any help would be nice thanks

---

### Post by Dogfighter on 2007-11-10
go via terminal into ur et directory, the give pbweb.x86 chmod +x .
then let it update.
after that copy pbweb.x86 into /home/username/.etwolf/pb and excute it there again.
no more pb kicks after that ;)

---

### Post by Molatove on 2007-11-10
Thanks  dogfighter game going fine

---

### Post by go_beep_yourself on 2007-12-09
Thanks. I had the same problem.

---

### Post by Codename47 on 2007-12-17
Awesome, finally i got my ET working properly =)

---

### Post by nipplecrippler on 2008-01-29
> **Dogfighter said:**
> go via terminal into ur et directory, the give pbweb.x86 chmod +x .
then let it update.
after that copy pbweb.x86 into /home/username/.etwolf/pb and excute it there again.
no more pb kicks after that ;)

I'm stuck on this one guys  :confused:

 - I have given executable permissions to pbweb.x86.
 - I've tried your method of updating in the ET folder first and then in the pb folder.
 - I enter game and am still kicked for this 20004 violation.

```
vege@ORAC:~/ET$ sudo ./pbweb.x86
[sudo] password for vege:
PBWEB v2.2
This program is (C) Copyright 2002-2005 by Even Balance, Inc., All Rights Reserved.

pbweb must be launched from the home "pb" folder where the game is installed.
If launched from another location, pbweb will not be able to update PunkBuster.

If you experience a problem with this program, please visit our support center
at http://www.evenbalance.com.

Starting pbweb to check for PunkBuster updates via world wide web
Initializing ... (please wait - ctrl+c to cancel)
Resolving www.evenbalance.com
Resolved to 64.34.201.5
Checking for PB Client updates
Game: et
Attempting to download pbsec.htm (please wait)
Received File pbsec.htm (1400 bytes)
Attempting to download htm/la001382.htm (please wait)
Received File la001382.htm (61321 bytes)
htm/la001382.htm successfully converted to dll/la001382.so
File already exists: htm/lc002036.htm
htm/lc002036.htm successfully converted to dll/lc002036.so
dll/lc002036.so copied to pbclnew.so
vege@ORAC:~/ET$ cd pb
vege@ORAC:~/ET/pb$ sudo ./pbweb.x86
PBWEB v2.2
This program is (C) Copyright 2002-2005 by Even Balance, Inc., All Rights Reserved.

pbweb must be launched from the home "pb" folder where the game is installed.
If launched from another location, pbweb will not be able to update PunkBuster.

If you experience a problem with this program, please visit our support center
at http://www.evenbalance.com.

Starting pbweb to check for PunkBuster updates via world wide web
Initializing ... (please wait - ctrl+c to cancel)
Resolving www.evenbalance.com
Resolved to 64.251.14.78
Checking for PB Client updates
Game: et
Attempting to download pbsec.htm (please wait)
Received File pbsec.htm (1400 bytes)
File already exists: htm/la001382.htm
htm/la001382.htm successfully converted to dll/la001382.so
File already exists: htm/lc002036.htm
htm/lc002036.htm successfully converted to dll/lc002036.so
dll/lc002036.so copied to pbclnew.so
Checking for PB Server updates
Game: et
Attempting to download pbsecsv.htm (please wait)
Received File pbsecsv.htm (1400 bytes)
File already exists: htm/ls001635.htm
htm/ls001635.htm successfully converted to dll/ls001635.so
dll/ls001635.so copied to pbsvnew.so
File already exists: htm/wa001382.htm
htm/wa001382.htm successfully converted to dll/wa001382.so
Removed dll/wa001382.so - not needed
File already exists: htm/la001382.htm
htm/la001382.htm successfully converted to dll/la001382.so
File already exists: htm/ma001382.htm
htm/ma001382.htm successfully converted to dll/ma001382.so
Removed dll/ma001382.so - not needed
File already exists: htm/wc002036.htm
htm/wc002036.htm successfully converted to dll/wc002036.so
Removed dll/wc002036.so - not needed
File already exists: htm/lc002036.htm
htm/lc002036.htm successfully converted to dll/lc002036.so
dll/lc002036.so copied to pbclnew.so
File already exists: htm/mc002036.htm
htm/mc002036.htm successfully converted to dll/mc002036.so
Removed dll/mc002036.so - not needed
pbclnew.so copied to pbclsnew.so
```

I had previously attempted to update via pb folder only.

I have used this pbsetup.exe tool from within Windows platform successfully, but I can't seem to use it here - ```
http://www.punkbuster.com/index.php?page=pbsetup.php
```

The instructions say - **For best results, users should create a folder on the hard drive to hold PBSetup and the various files that it will create and use during operation. PBSetup should be downloaded directly into the folder or moved into the folder after downloading to the desktop but before running PBSetup for the first time.**

I have trouble getting this to do anything  :(

I have set this pbsetup.run file up inside this structure -

```
Home > ET > pb > pbsetup
```

```
vege@ORAC:~$ cd ET
vege@ORAC:~/ET$ cd pb
vege@ORAC:~/ET/pb$ cd pbsetup
vege@ORAC:~/ET/pb/pbsetup$ sudo ./pbsetup.run
vege@ORAC:~/ET/pb/pbsetup$
```

Help would be so greatly appreciated .

---

### Post by nipplecrippler on 2008-01-30
OK, my problem is resolved  :)

As dogfighter said, the solution is to update pbweb.x86 via the 2 different directories.

**/usr/local/games/enemy-territory/pb**  (or whichever directory you installed the game to)

**/.etwolf/pb**  (which is hidden)

pbweb.x86 needs to be in both directories and once updated the error message is fixed.

Thanks to dogfighter and to [email]px33@ubuntu.pl[/email], here - [http://ubuntuforums.org/showpost.php?p=3588335&postcount=269](http://ubuntuforums.org/showpost.php?p=3588335&postcount=269)

---

### Post by Shadowmeph on 2008-02-19
> **nipplecrippler said:**
> OK, my problem is resolved  :)

As dogfighter said, the solution is to update pbweb.x86 via the 2 different directories.

**/usr/local/games/enemy-territory/pb**  (or whichever directory you installed the game to)

**/.etwolf/pb**  (which is hidden)

pbweb.x86 needs to be in both directories and once updated the error message is fixed.

Thanks to dogfighter and to [email]px33@ubuntu.pl[/email], here - [http://ubuntuforums.org/showpost.php?p=3588335&postcount=269](http://ubuntuforums.org/showpost.php?p=3588335&postcount=269)

I did this and get the same error as before

---

### Post by applezip on 2009-12-15
> **nipplecrippler said:**
> I'm stuck on this one guys  :confused:

 - I have given executable permissions to pbweb.x86.
 - I've tried your method of updating in the ET folder first and then in the pb folder.
 - I enter game and am still kicked for this 20004 violation.

```
vege@ORAC:~/ET$ sudo ./pbweb.x86
[sudo] password for vege:
PBWEB v2.2
This program is (C) Copyright 2002-2005 by Even Balance, Inc., All Rights Reserved.

pbweb must be launched from the home "pb" folder where the game is installed.
If launched from another location, pbweb will not be able to update PunkBuster.

If you experience a problem with this program, please visit our support center
at http://www.evenbalance.com.

Starting pbweb to check for PunkBuster updates via world wide web
Initializing ... (please wait - ctrl+c to cancel)
Resolving www.evenbalance.com
Resolved to 64.34.201.5
Checking for PB Client updates
Game: et
Attempting to download pbsec.htm (please wait)
Received File pbsec.htm (1400 bytes)
Attempting to download htm/la001382.htm (please wait)
Received File la001382.htm (61321 bytes)
htm/la001382.htm successfully converted to dll/la001382.so
File already exists: htm/lc002036.htm
htm/lc002036.htm successfully converted to dll/lc002036.so
dll/lc002036.so copied to pbclnew.so
vege@ORAC:~/ET$ cd pb
vege@ORAC:~/ET/pb$ sudo ./pbweb.x86
PBWEB v2.2
This program is (C) Copyright 2002-2005 by Even Balance, Inc., All Rights Reserved.

pbweb must be launched from the home "pb" folder where the game is installed.
If launched from another location, pbweb will not be able to update PunkBuster.

If you experience a problem with this program, please visit our support center
at http://www.evenbalance.com.

Starting pbweb to check for PunkBuster updates via world wide web
Initializing ... (please wait - ctrl+c to cancel)
Resolving www.evenbalance.com
Resolved to 64.251.14.78
Checking for PB Client updates
Game: et
Attempting to download pbsec.htm (please wait)
Received File pbsec.htm (1400 bytes)
File already exists: htm/la001382.htm
htm/la001382.htm successfully converted to dll/la001382.so
File already exists: htm/lc002036.htm
htm/lc002036.htm successfully converted to dll/lc002036.so
dll/lc002036.so copied to pbclnew.so
Checking for PB Server updates
Game: et
Attempting to download pbsecsv.htm (please wait)
Received File pbsecsv.htm (1400 bytes)
File already exists: htm/ls001635.htm
htm/ls001635.htm successfully converted to dll/ls001635.so
dll/ls001635.so copied to pbsvnew.so
File already exists: htm/wa001382.htm
htm/wa001382.htm successfully converted to dll/wa001382.so
Removed dll/wa001382.so - not needed
File already exists: htm/la001382.htm
htm/la001382.htm successfully converted to dll/la001382.so
File already exists: htm/ma001382.htm
htm/ma001382.htm successfully converted to dll/ma001382.so
Removed dll/ma001382.so - not needed
File already exists: htm/wc002036.htm
htm/wc002036.htm successfully converted to dll/wc002036.so
Removed dll/wc002036.so - not needed
File already exists: htm/lc002036.htm
htm/lc002036.htm successfully converted to dll/lc002036.so
dll/lc002036.so copied to pbclnew.so
File already exists: htm/mc002036.htm
htm/mc002036.htm successfully converted to dll/mc002036.so
Removed dll/mc002036.so - not needed
pbclnew.so copied to pbclsnew.so
```

I had previously attempted to update via pb folder only.

I have used this pbsetup.exe tool from within Windows platform successfully, but I can't seem to use it here - ```
http://www.punkbuster.com/index.php?page=pbsetup.php
```

The instructions say - **For best results, users should create a folder on the hard drive to hold PBSetup and the various files that it will create and use during operation. PBSetup should be downloaded directly into the folder or moved into the folder after downloading to the desktop but before running PBSetup for the first time.**

I have trouble getting this to do anything  :(

I have set this pbsetup.run file up inside this structure -

```
Home > ET > pb > pbsetup
```

```
vege@ORAC:~$ cd ET
vege@ORAC:~/ET$ cd pb
vege@ORAC:~/ET/pb$ cd pbsetup
vege@ORAC:~/ET/pb/pbsetup$ sudo ./pbsetup.run
vege@ORAC:~/ET/pb/pbsetup$
```

Help would be so greatly appreciated .

This is a really late reply, but whatever.

When you download pbsetup, it does not know to update ET.

./pbsetup.run -ag et
./pbsetup.run -u

This will update ET. If it can't find the installation you can specify.

---

