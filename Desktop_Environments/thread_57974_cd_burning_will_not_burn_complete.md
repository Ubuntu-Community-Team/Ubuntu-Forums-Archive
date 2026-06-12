---
title: "cd burning will not burn complete"
date: 2005-08-18
forum: Desktop Environments
---

### Post by kennny2004 on 2005-08-18
Hi i got the new Ubuntu and staff i am kinda new with linux but i know some of the Unix commands and staff but don't know about applications and the gnome desktop but the problem is that i got few *.iso files so they are images already and i tried burning them on a cd but it does not burn completly like the *.iso files is 600mb it will burn like 123mb then stop does anyone know why it is doing this? ](*,) 
ooo ya and my cd rw is AOPEN  - CD-RW CRW4048
 and i have tried diffirent cd applications like the default one and the k3b tryed to get soemmore to work but i got to many problems installing them with all the errors ( and it is wierd because all the packages i have installed but still get errors)
Thanks for all your help. O:)  :-)  :)

---

### Post by kennny2004 on 2005-08-18
bump.,

---

### Post by tag on 2005-08-18
In this case it seems very likely that the problem you are experiencing has something to do with the errors you get while installing, or using these applications. Please post them here on the forum so we can see what the problem is.

---

### Post by kennny2004 on 2005-08-18
Ummm i get no errors... well not that i know of. liek the default gnome burner just it says burning and the bar is going then at like 1/4 it stops changes to fixating then that stays for a while and finishes. with k3b it almost finishes like 95% then it changes to fixating and fixating does not finish and are there any log i can chack out for the errors? Thanks for that reply

---

### Post by kennny2004 on 2005-08-19
bump

---

### Post by jyank on 2005-08-19
Might want to try maybe slowing the speed down while you're burning.

If you haven't tried the program GnomeBaker yet, I'd highly reccomend using it.  Worked flawlessly for me without having to tweak anything.

---

### Post by kennny2004 on 2005-08-19
thanks for that reply and i will try it and then let u know how it was ( get install is the best thing ever i can get anything)

---

### Post by kennny2004 on 2005-08-19
k i tried with gnomebaker and speed of 5 and here what the error said:

Track 01:  414 of  637 MB written (fifo  98%) [buf  95%]   8.4x.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 03 3C E3 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 03 3C E4 0C 00 00 00 00 10 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x10 Qual 0x02 (id crc or ecc error) [No matching qualifier] Fru 0x0
Sense flags: Blk 212196 (valid) 
resid: 63488
cmd finished after 0.017s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 434575360 bytes
Writing  time:  366.023s
Average write speed  12.0x.
Min drive buffer fill was 78%
Fixating...
Fixating time:   32.853s
cdrecord: fifo had 6909 puts and 6846 gets.
cdrecord: fifo was 0 times empty and 3595 times full, min fill was 84%.
(that was in the windows in the baker)
I don't think nothing important was in the terminal but if u guys need i can post it and i do not think something wron with the file because
1. It is always diffirent place
2. i tryed at least 6 diffirent things to burn

Could it be the cd's are shit? they are imiation Cd-r 52x for music data video games
anything else u guys need let me now and thanks for helping me

---

### Post by kennny2004 on 2005-08-19
bump

---

### Post by FLeiXiuS on 2005-08-19
Looks like a bad burn.  The "Read" error signifies that.  Try redownloading the ISO.

---

### Post by FLeiXiuS on 2005-08-19
Looks like a bad burn.  The "Read" error signifies that.  Try redownloading the ISO.  

You may also try enabling DMA.  This will most likely improve performance of your cdrom drive.  

$ hdparm -d1 /dev/cdrom

---

### Post by kennny2004 on 2005-08-20
thanks for suggestin but i tryed dling like 6 diffirent files but i will try thta things thanks

---

