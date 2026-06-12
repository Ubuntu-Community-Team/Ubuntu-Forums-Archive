---
title: "Serious Hard Drives Errors"
date: 2009-02-14
forum: General Help
---

### Post by pbeesley on 2009-02-14
Right I'm fighting to keep my hard drive data is long gone, just want it working again. When trying to mount I'm told it has an error 
```
kp3@sol:~$ sudo mount /dev/sda2 /media/Jupiter
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

However my output of fsck -v -y /dev/sda2 is below
```
kp3@sol:~$ sudo fsck /dev/sda2 -y -v
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Group descriptors look bad... trying backup blocks...
Inode table for group 570 is not in group.  (block 18644994)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 571 is not in group.  (block 18677760)
Relocate? yes

Inode bitmap for group 571 is not in group.  (block 18677761)
Relocate? yes

Inode table for group 571 is not in group.  (block 18644994)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 572 is not in group.  (block 18677760)
Relocate? yes

Inode bitmap for group 572 is not in group.  (block 18677761)
Relocate? yes

Block bitmap for group 573 is not in group.  (block 18677760)
Relocate? yes

Inode bitmap for group 573 is not in group.  (block 18677761)
Relocate? yes

Inode table for group 573 is not in group.  (block 18743298)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 1759 is not in group.  (block 57606144)
Relocate? yes

Inode bitmap for group 1759 is not in group.  (block 57606145)
Relocate? yes

Inode table for group 1759 is not in group.  (block 57606146)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

kp3@sol:~$ sudo fsck /dev/sda2 -y -v
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Group descriptors look bad... trying backup blocks...
Inode table for group 570 is not in group.  (block 18644994)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 571 is not in group.  (block 18677760)
Relocate? yes

Inode bitmap for group 571 is not in group.  (block 18677761)
Relocate? yes

Inode table for group 571 is not in group.  (block 18644994)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 572 is not in group.  (block 18677760)
Relocate? yes

Inode bitmap for group 572 is not in group.  (block 18677761)
Relocate? yes

Block bitmap for group 573 is not in group.  (block 18677760)
Relocate? yes

Inode bitmap for group 573 is not in group.  (block 18677761)
Relocate? yes

Inode table for group 573 is not in group.  (block 18743298)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 1759 is not in group.  (block 57606144)
Relocate? yes

Inode bitmap for group 1759 is not in group.  (block 57606145)
Relocate? yes

Inode table for group 1759 is not in group.  (block 57606146)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

  Block bitmap at 91881472 (+0), Inode bitmap at 91881473 (+1)
  Inode table at 91881474-91881729 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 91881730-91914239
  Free inodes: 22970369-22978560
Group 2805: (Blocks 91914240-91947007)
  Block bitmap at 91914240 (+0), Inode bitmap at 91914241 (+1)
  Inode table at 91914242-91914497 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 91914498-91947007
  Free inodes: 22978561-22986752
Group 2806: (Blocks 91947008-91979775)
  Block bitmap at 91947008 (+0), Inode bitmap at 91947009 (+1)
  Inode table at 91947010-91947265 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 91947266-91979775
  Free inodes: 22986753-22994944
Group 2807: (Blocks 91979776-92012543)
  Block bitmap at 91979776 (+0), Inode bitmap at 91979777 (+1)
  Inode table at 91979778-91980033 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 91980034-92012543
  Free inodes: 22994945-23003136
Group 2808: (Blocks 92012544-92045311)
  Block bitmap at 92012544 (+0), Inode bitmap at 92012545 (+1)
  Inode table at 92012546-92012801 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92012802-92045311
  Free inodes: 23003137-23011328
Group 2809: (Blocks 92045312-92078079)
  Block bitmap at 92045312 (+0), Inode bitmap at 92045313 (+1)
  Inode table at 92045314-92045569 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92045570-92078079
  Free inodes: 23011329-23019520
Group 2810: (Blocks 92078080-92110847)
  Block bitmap at 92078080 (+0), Inode bitmap at 92078081 (+1)
  Inode table at 92078082-92078337 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92078338-92110847
  Free inodes: 23019521-23027712
Group 2811: (Blocks 92110848-92143615)
  Block bitmap at 92110848 (+0), Inode bitmap at 92110849 (+1)
  Inode table at 92110850-92111105 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92111106-92143615
  Free inodes: 23027713-23035904
Group 2812: (Blocks 92143616-92176383)
  Block bitmap at 92143616 (+0), Inode bitmap at 92143617 (+1)
  Inode table at 92143618-92143873 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92143874-92176383
  Free inodes: 23035905-23044096
Group 2813: (Blocks 92176384-92209151)
  Block bitmap at 92176384 (+0), Inode bitmap at 92176385 (+1)
  Inode table at 92176386-92176641 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92176642-92209151
  Free inodes: 23044097-23052288
Group 2814: (Blocks 92209152-92241919)
  Block bitmap at 92209152 (+0), Inode bitmap at 92209153 (+1)
  Inode table at 92209154-92209409 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92209410-92241919
  Free inodes: 23052289-23060480
Group 2815: (Blocks 92241920-92274687)
  Block bitmap at 92241920 (+0), Inode bitmap at 92241921 (+1)
  Inode table at 92241922-92242177 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92242178-92274687
  Free inodes: 23060481-23068672
Group 2816: (Blocks 92274688-92307455)
  Block bitmap at 92274688 (+0), Inode bitmap at 92274689 (+1)
  Inode table at 92274690-92274945 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92274946-92307455
  Free inodes: 23068673-23076864
Group 2817: (Blocks 92307456-92340223)
  Block bitmap at 92307456 (+0), Inode bitmap at 92307457 (+1)
  Inode table at 92307458-92307713 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92307714-92340223
  Free inodes: 23076865-23085056
Group 2818: (Blocks 92340224-92372991)
  Block bitmap at 92340224 (+0), Inode bitmap at 92340225 (+1)
  Inode table at 92340226-92340481 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92340482-92372991
  Free inodes: 23085057-23093248
Group 2819: (Blocks 92372992-92405759)
  Block bitmap at 92372992 (+0), Inode bitmap at 92372993 (+1)
  Inode table at 92372994-92373249 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92373250-92405759
  Free inodes: 23093249-23101440
Group 2820: (Blocks 92405760-92438527)
  Block bitmap at 92405760 (+0), Inode bitmap at 92405761 (+1)
  Inode table at 92405762-92406017 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92406018-92438527
  Free inodes: 23101441-23109632
Group 2821: (Blocks 92438528-92471295)
  Block bitmap at 92438528 (+0), Inode bitmap at 92438529 (+1)
  Inode table at 92438530-92438785 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92438786-92471295
  Free inodes: 23109633-23117824
Group 2822: (Blocks 92471296-92504063)
  Block bitmap at 92471296 (+0), Inode bitmap at 92471297 (+1)
  Inode table at 92471298-92471553 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92471554-92504063
  Free inodes: 23117825-23126016
Group 2823: (Blocks 92504064-92536831)
  Block bitmap at 92504064 (+0), Inode bitmap at 92504065 (+1)
  Inode table at 92504066-92504321 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92504322-92536831
  Free inodes: 23126017-23134208
Group 2824: (Blocks 92536832-92569599)
  Block bitmap at 92536832 (+0), Inode bitmap at 92536833 (+1)
  Inode table at 92536834-92537089 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92537090-92569599
  Free inodes: 23134209-23142400
Group 2825: (Blocks 92569600-92602367)
  Block bitmap at 92569600 (+0), Inode bitmap at 92569601 (+1)
  Inode table at 92569602-92569857 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92569858-92602367
  Free inodes: 23142401-23150592
Group 2826: (Blocks 92602368-92635135)
  Block bitmap at 92602368 (+0), Inode bitmap at 92602369 (+1)
  Inode table at 92602370-92602625 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92602626-92635135
  Free inodes: 23150593-23158784
Group 2827: (Blocks 92635136-92667903)
  Block bitmap at 92635136 (+0), Inode bitmap at 92635137 (+1)
  Inode table at 92635138-92635393 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92635394-92667903
  Free inodes: 23158785-23166976
Group 2828: (Blocks 92667904-92700671)
  Block bitmap at 92667904 (+0), Inode bitmap at 92667905 (+1)
  Inode table at 92667906-92668161 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92668162-92700671
  Free inodes: 23166977-23175168
Group 2829: (Blocks 92700672-92733439)
  Block bitmap at 92700672 (+0), Inode bitmap at 92700673 (+1)
  Inode table at 92700674-92700929 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92700930-92733439
  Free inodes: 23175169-23183360
Group 2830: (Blocks 92733440-92766207)
  Block bitmap at 92733440 (+0), Inode bitmap at 92733441 (+1)
  Inode table at 92733442-92733697 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92733698-92766207
  Free inodes: 23183361-23191552
Group 2831: (Blocks 92766208-92798975)
  Block bitmap at 92766208 (+0), Inode bitmap at 92766209 (+1)
  Inode table at 92766210-92766465 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92766466-92798975
  Free inodes: 23191553-23199744
Group 2832: (Blocks 92798976-92831743)
  Block bitmap at 92798976 (+0), Inode bitmap at 92798977 (+1)
  Inode table at 92798978-92799233 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92799234-92831743
  Free inodes: 23199745-23207936
Group 2833: (Blocks 92831744-92864511)
  Block bitmap at 92831744 (+0), Inode bitmap at 92831745 (+1)
  Inode table at 92831746-92832001 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92832002-92864511
  Free inodes: 23207937-23216128
Group 2834: (Blocks 92864512-92897279)
  Block bitmap at 92864512 (+0), Inode bitmap at 92864513 (+1)
  Inode table at 92864514-92864769 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92864770-92897279
  Free inodes: 23216129-23224320
Group 2835: (Blocks 92897280-92930047)
  Block bitmap at 92897280 (+0), Inode bitmap at 92897281 (+1)
  Inode table at 92897282-92897537 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92897538-92930047
  Free inodes: 23224321-23232512
Group 2836: (Blocks 92930048-92962815)
  Block bitmap at 92930048 (+0), Inode bitmap at 92930049 (+1)
  Inode table at 92930050-92930305 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92930306-92962815
  Free inodes: 23232513-23240704
Group 2837: (Blocks 92962816-92995583)
  Block bitmap at 92962816 (+0), Inode bitmap at 92962817 (+1)
  Inode table at 92962818-92963073 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92963074-92995583
  Free inodes: 23240705-23248896
Group 2838: (Blocks 92995584-93028351)
  Block bitmap at 92995584 (+0), Inode bitmap at 92995585 (+1)
  Inode table at 92995586-92995841 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 92995842-93028351
  Free inodes: 23248897-23257088
Group 2839: (Blocks 93028352-93061119)
  Block bitmap at 93028352 (+0), Inode bitmap at 93028353 (+1)
  Inode table at 93028354-93028609 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93028610-93061119
  Free inodes: 23257089-23265280
Group 2840: (Blocks 93061120-93093887)
  Block bitmap at 93061120 (+0), Inode bitmap at 93061121 (+1)
  Inode table at 93061122-93061377 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93061378-93093887
  Free inodes: 23265281-23273472
Group 2841: (Blocks 93093888-93126655)
  Block bitmap at 93093888 (+0), Inode bitmap at 93093889 (+1)
  Inode table at 93093890-93094145 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93094146-93126655
  Free inodes: 23273473-23281664
Group 2842: (Blocks 93126656-93159423)
  Block bitmap at 93126656 (+0), Inode bitmap at 93126657 (+1)
  Inode table at 93126658-93126913 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93126914-93159423
  Free inodes: 23281665-23289856
Group 2843: (Blocks 93159424-93192191)
  Block bitmap at 93159424 (+0), Inode bitmap at 93159425 (+1)
  Inode table at 93159426-93159681 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93159682-93192191
  Free inodes: 23289857-23298048
Group 2844: (Blocks 93192192-93224959)
  Block bitmap at 93192192 (+0), Inode bitmap at 93192193 (+1)
  Inode table at 93192194-93192449 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93192450-93224959
  Free inodes: 23298049-23306240
Group 2845: (Blocks 93224960-93257727)
  Block bitmap at 93224960 (+0), Inode bitmap at 93224961 (+1)
  Inode table at 93224962-93225217 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93225218-93257727
  Free inodes: 23306241-23314432
Group 2846: (Blocks 93257728-93290495)
  Block bitmap at 93257728 (+0), Inode bitmap at 93257729 (+1)
  Inode table at 93257730-93257985 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93257986-93290495
  Free inodes: 23314433-23322624
Group 2847: (Blocks 93290496-93323263)
  Block bitmap at 93290496 (+0), Inode bitmap at 93290497 (+1)
  Inode table at 93290498-93290753 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93290754-93323263
  Free inodes: 23322625-23330816
Group 2848: (Blocks 93323264-93356031)
  Block bitmap at 93323264 (+0), Inode bitmap at 93323265 (+1)
  Inode table at 93323266-93323521 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93323522-93356031
  Free inodes: 23330817-23339008
Group 2849: (Blocks 93356032-93388799)
  Block bitmap at 93356032 (+0), Inode bitmap at 93356033 (+1)
  Inode table at 93356034-93356289 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93356290-93388799
  Free inodes: 23339009-23347200
Group 2850: (Blocks 93388800-93421567)
  Block bitmap at 93388800 (+0), Inode bitmap at 93388801 (+1)
  Inode table at 93388802-93389057 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93389058-93421567
  Free inodes: 23347201-23355392
Group 2851: (Blocks 93421568-93454335)
  Block bitmap at 93421568 (+0), Inode bitmap at 93421569 (+1)
  Inode table at 93421570-93421825 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93421826-93454335
  Free inodes: 23355393-23363584
Group 2852: (Blocks 93454336-93487103)
  Block bitmap at 93454336 (+0), Inode bitmap at 93454337 (+1)
  Inode table at 93454338-93454593 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93454594-93487103
  Free inodes: 23363585-23371776
Group 2853: (Blocks 93487104-93519871)
  Block bitmap at 93487104 (+0), Inode bitmap at 93487105 (+1)
  Inode table at 93487106-93487361 (+2)
  32510 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93487362-93519871
  Free inodes: 23371777-23379968
Group 2854: (Blocks 93519872-93542477)
  Block bitmap at 93519872 (+0), Inode bitmap at 93519873 (+1)
  Inode table at 93519874-93520129 (+2)
  22348 free blocks, 8192 free inodes, 0 directories
  Free blocks: 93520130-93542477
  Free inodes: 23379969-23388160
kp3@sol:~$ sudo fsck /dev/sda2 -y -v
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Group descriptors look bad... trying backup blocks...
Inode table for group 570 is not in group.  (block 18644994)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 571 is not in group.  (block 18677760)
Relocate? yes

Inode bitmap for group 571 is not in group.  (block 18677761)
Relocate? yes

Inode table for group 571 is not in group.  (block 18644994)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 572 is not in group.  (block 18677760)
Relocate? yes

Inode bitmap for group 572 is not in group.  (block 18677761)
Relocate? yes

Block bitmap for group 573 is not in group.  (block 18677760)
Relocate? yes

Inode bitmap for group 573 is not in group.  (block 18677761)
Relocate? yes

Inode table for group 573 is not in group.  (block 18743298)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 1759 is not in group.  (block 57606144)
Relocate? yes

Inode bitmap for group 1759 is not in group.  (block 57606145)
Relocate? yes

Inode table for group 1759 is not in group.  (block 57606146)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

/dev/sda2 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 7, i_blocks is 136144, should be 136224.  Fix? yes

Relocating group 570's inode table to 18677762...
Relocating group 571's block bitmap to 18710528...
Relocating group 571's inode bitmap to 18710529...
Relocating group 571's inode table to 18710530...
Relocating group 572's block bitmap to 18743296...
Relocating group 572's inode bitmap to 18743297...
Relocating group 573's block bitmap to 18776064...
Relocating group 573's inode bitmap to 18776065...
Relocating group 573's inode table to 18776066...
Relocating group 1759's block bitmap to 57638912...
Relocating group 1759's inode bitmap to 57638913...
Relocating group 1759's inode table to 57638914...
Restarting e2fsck from the beginning...
fsck.ext3: Group descriptors look bad... trying backup blocks...
Inode table for group 1648 is not in group.  (block 53968898)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 1649 is not in group.  (block 54001664)
Relocate? yes

Inode bitmap for group 1649 is not in group.  (block 54001665)
Relocate? yes

Inode table for group 1649 is not in group.  (block 53968898)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Inode table for group 2800 is not in group.  (block 91717634)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 2802 is not in group.  (block 91783168)
Relocate? yes

Inode bitmap for group 2802 is not in group.  (block 91783169)
Relocate? yes

Inode table for group 2802 is not in group.  (block 91783170)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 2803 is not in group.  (block 91783168)
Relocate? yes

Inode bitmap for group 2803 is not in group.  (block 91783169)
Relocate? yes

Inode table for group 2803 is not in group.  (block 91783170)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 2804 is not in group.  (block 91783168)
Relocate? yes

Inode bitmap for group 2804 is not in group.  (block 91783169)
Relocate? yes

Block bitmap for group 2805 is not in group.  (block 91783168)
Relocate? yes

Inode bitmap for group 2805 is not in group.  (block 91783169)
Relocate? yes

Block bitmap for group 2806 is not in group.  (block 91783168)
Relocate? yes

Inode bitmap for group 2806 is not in group.  (block 91783169)
Relocate? yes

/dev/sda2 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Relocating group 1648's inode table to 54001666...
Relocating group 1649's block bitmap to 54034432...
Relocating group 1649's inode bitmap to 54034433...
Relocating group 1649's inode table to 54034434...
Relocating group 2800's inode table to 91750402...
Relocating group 2802's block bitmap to 91815936...
Relocating group 2802's inode bitmap to 91815937...
Relocating group 2802's inode table to 91815938...
Relocating group 2803's block bitmap to 91848704...
Relocating group 2803's inode bitmap to 91848705...
Relocating group 2803's inode table to 91848706...
Relocating group 2804's block bitmap to 91881472...
Relocating group 2804's inode bitmap to 91881473...
Relocating group 2805's block bitmap to 91914240...
Relocating group 2805's inode bitmap to 91914241...
Relocating group 2806's block bitmap to 91947008...
Relocating group 2806's inode bitmap to 91947009...
Restarting e2fsck from the beginning...
fsck.ext3: Group descriptors look bad... trying backup blocks...
Block bitmap for group 732 is not in group.  (block 23953408)
Relocate? yes

Inode bitmap for group 732 is not in group.  (block 23953409)
Relocate? yes

Inode table for group 732 is not in group.  (block 23953410)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 733 is not in group.  (block 23953408)
Relocate? yes

Inode bitmap for group 733 is not in group.  (block 23953409)
Relocate? yes

Inode table for group 733 is not in group.  (block 23953410)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Inode table for group 1918 is not in group.  (block 62816258)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Inode table for group 1919 is not in group.  (block 62816258)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 1920 is not in group.  (block 62881792)
Relocate? yes

Inode bitmap for group 1920 is not in group.  (block 62881793)
Relocate? yes

Inode table for group 1920 is not in group.  (block 62816258)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate? yes

Block bitmap for group 1921 is not in group.  (block 62881792)
Relocate? yes

Inode bitmap for group 1921 is not in group.  (block 62881793)
Relocate? yes

/dev/sda2 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
/dev/sda2: e2fsck cancelled.

/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****

```

Anyone able to help? What do you need to know :(

Thanks in advance :confused:

---

### Post by pbeesley on 2009-02-14
running again with -f

---

### Post by pbeesley on 2009-02-14
no help?

---

### Post by pbeesley on 2009-02-16
no one :|

---

