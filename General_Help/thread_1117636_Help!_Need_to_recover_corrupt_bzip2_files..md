---
title: "Help! Need to recover corrupt bzip2 files."
date: 2009-04-06
forum: General Help
---

### Post by afrodeity on 2009-04-06
I have a corrupted 1.3 gig torrent bz2 archive that I am trying to recover data from.

I found this [debian tutorial]("https://www.linuxquestions.org/questions/linux-general-1/help-need-to-recover-corrupt-bzip2-files..-289800/") but am a little stuck. Any way around the problem. Please see my comments in red.

1. Use bzip2recover to recover the individual bzip2 blocks (900k by default)
# bzip2recover corrupt.tar.bz2

which gernerates chunks:
rec00001backup.tar.bz2
rec00002backup.tar.bz2
rec00003backup.tar.bz2
etc..

2. Send bzip2 test results to a file for searching
(could also grep right here if you want):
#for i in *.bz2; do bzip2 -tvf $i >> corruptblocks.out 2>&1; done

3. Search the test results for errors
# grep -i CRC corruptblocks.out

4. Delete the corrupt block
# rm <corruptblock>.tar.bz2

5. Untar all of the bzip2 blocks elsewhere
# for i in *.bz2; do bzip2 -dcvf $i > /elsewhere/$i.tar; done

[COLOR="Red"]>If i try to run the above, i get: /elsewhere/rec00455tiger-x86.tar.bz2.tar: Permission denied
> If i run as root -I AM STUCK WITH THIS ERROR:
> syntax error near unexpected token `do'[/COLOR]


6. Here you need to look for the first occurence of a tar header prior to the corrupt block. A tar block basically consists of the tar header filename (eg the actual file archived - /pictures/easter/pic02.jpg), followed by tar header metadata (doesn't matter), followed by the actual data. A tar archive is just made up of sequential tar blocks. The aim is to remove the entire tar block in which the corrupt bzip2 block lived. The untaring will continue as if the corrupt tar block never existed.

I did it using a hex editor as I wasn't too sure in which actual file (from the filesystem) the error had occured. So if the corruption occurred in block 1000, I would check through block 999, then 998 etc... If you know that you were backing up the "/pictures" directory and it failed around the "/pictures/easter" directory, then greping for "/pictures/easter" in the few blocks prior should find a match. You need to do the same to find the closest tar header AFTER the corrupt block. Remember that it needs to be just the tar block in which the corruption occured.

Eg.
block997.tar - Closest preceeding header (/pictures/easter/pic01.jpg)
block998.tar
block999.tar
block1000.tar - CORRUPT BLOCK
block1001.tar
block1002.tar - Closest trailing header (/pictures/easter/pic02.jpg)

a. Here you would open block997.tar and remove ALL data from the start of the header (/pictures/easter/pic01.jpg......) to the end of the file (the first "/" char onwards).
b. Make sure you delete block998.tar, block999.tar, block1000.tar (should have already been deleted earlier) and block1001.tar.
c. Open block1002.tar and remove ALL data from the byte prior to the start of the next header (/pictures/easter/pic02.jpg) to the start of the file (the new file should now start with /pictures/easter/pic02.jpg as opposed to raw data)

(After this, the tar block with the corrupt data should have been removed)

7. Glue everything back together using:
# cat /elsewhere/*.tar > recovered.tar

8. Untar as usual to recover existing data
* tar -xvf recovered

---

### Post by coffeecat on 2009-04-06
You might have more success with [this tutorial]("http://www.bestsolution.at/support/console/repair_tar_archives.html.en"). It looks superficially the same, but it contains this important bit:

>                      Tar claims to have the feature to scan even corrupt files for tar headers                     in it but this feature has one major blemish: It only works, if no bytes are                     lost in the file because tar scans expects file headers to be 512 bytes in                      size. If only one byte is lost in such a header (or a following data block),                     this "recovery feature" fails and becomes an annoyance.                     
                                           Luck returned a couple of weeks later when I received an email from a nice                     guy that had written a nice perl script that really searched a file for a                     tar header bytewise and not in the 512 bytes manner of tar itself. You can                     [download it here]("http://www.bestsolution.at/documents/find_tar_headers.pl.bz2").
You need the perl script. With it I managed to stitch together a damaged bzip2 and the only thing I lost was the single corrupted rec* fragment somewhere in the middle.

---

### Post by afrodeity on 2009-04-06
Sorry to sound like a Noob, but how do i run the perl script on the archive. Do I have to have it in the same directory? ./ or something?

---

### Post by coffeecat on 2009-04-06
If you look a bit below the part I quoted, you'll see that he used:

```
**% perl find_tar_headers.pl good_tail.tar**
```so you must be in the same directory as the script and the good_tail.tar file, or whatever you choose to call it. Bear in mind that you need some perl stuff installed first. It's been some time since I had to run this but I seem to remember that when I ran it without all the necessary perl stuff, the errors told me what I needed to install first.

---

### Post by afrodeity on 2009-04-06
Don't know what happened, but something worked. I have a working archive.

This also seems like a good option:

bzip2 -dc rec*.bz2 > newdatafile

thanks for the help.

---

