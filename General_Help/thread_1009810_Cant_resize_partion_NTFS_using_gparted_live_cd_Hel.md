---
title: "Cant resize partion NTFS using gparted live cd Help"
date: 2008-12-13
forum: General Help
---

### Post by halfbakedoreo on 2008-12-13
Hi, i am very new to ubuntu and have tried resizing my ntfs partition using the gparted live cd and i get the following error after trying everything suggested to other people (chkdsk /r etc...) "An error occurred while applying the operations" and it asks me to save my details so i did and here is the out put.

Thanks in advance :)

GParted 0.3.8

Libparted 1.8.9

Shrink /dev/sda1 from 138.63 GiB to 128.86 GiB  00:00:18    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 290728304
size: 290728242 (138.63 GiB)
calculate new size and position of /dev/sda1  00:00:00    ( SUCCESS )
     	
requested start: 63
requested end: 270245429
requested size: 270245367 (128.86 GiB)
new start: 63
new end: 270245429
new size: 270245367 (128.86 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00:05    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 148852855296 bytes (148853 MB)
Current device size: 148852859904 bytes (148853 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 51804 MB (34.8%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 146831 MB 0
Multi-Record : 148691 MB 23154
$MFTMirr : 80016 MB 1
Compressed : 148566 MB 226442
Sparse : 88465 MB 19959
Ordinary : 148842 MB 25921
You might resize at 51803467776 bytes or 51804 MB (freeing 97049 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem  00:00:07    ( ERROR )
     	
run simulation  00:00:07    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1 -s 138365627903 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 148852855296 bytes (148853 MB)
Current device size: 148852859904 bytes (148853 MB)
New volume size : 138365620736 bytes (138366 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 51804 MB (34.8%)
Collecting resizing constraints ...
Needed relocations : 809730 (3317 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1032 > 1024), not yet supported!
Please try to free less space.
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00:05    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 148852855296 bytes (148853 MB)
Current device size: 148852859904 bytes (148853 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 51804 MB (34.8%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 146831 MB 0
Multi-Record : 148691 MB 23154
$MFTMirr : 80016 MB 1
Compressed : 148566 MB 226442
Sparse : 88465 MB 19959
Ordinary : 148842 MB 25921
You might resize at 51803467776 bytes or 51804 MB (freeing 97049 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:00:01    ( SUCCESS )
     	
run simulation  00:00:01    ( SUCCESS )
     	
ntfsresize -P --force --force /dev/sda1 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 148852855296 bytes (148853 MB)
Current device size: 148852859904 bytes (148853 MB)
New volume size : 148852855296 bytes (148853 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force --force /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 148852855296 bytes (148853 MB)
Current device size: 148852859904 bytes (148853 MB)
New volume size : 148852855296 bytes (148853 MB)
Nothing to do: NTFS volume size is already OK.

========================================

---

