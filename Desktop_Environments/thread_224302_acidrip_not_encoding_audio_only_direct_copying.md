---
title: "acidrip not encoding audio only direct copying"
date: 2006-07-27
forum: Desktop Environments
---

### Post by mikeym on 2006-07-27
Hi,

I'm using acidrip to encode from a DVD in 3 passes and I have selected to encode the audio from the second track on the DVD but whilst it creates the frameno.avi with the correct audio track once the final avi file is complete it has the wrong audio again.

Here is the Exported acidrip file I am running:

```

#!/bin/sh
echo "***********************************************************"
echo "Automated script created by AcidRip - http://acidrip.sf.net"
echo "***********************************************************"
unlink frameno.avi 2> /dev/null
mencoder dvd://1 -chapter 1-9 -oac mp3lame -lameopts abr:br=128 -aid 129  -ovc frameno -o frameno.avi
mencoder dvd://1 -chapter 1-9 -sid 0 -vobsubout /home/mikey/MyFile-1 -info srcform="DVD ripped by acidrip.sf.net":name="My Thing" -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=1761:vpass=1 -vf pp=de,crop=688:368:20:56,scale=640:-2   -ffourcc DX50 -o "/dev/null"
mencoder dvd://1 -chapter 1-9 -sid 0 -vobsubout /home/mikey/MyFile-1 -info srcform="DVD ripped by acidrip.sf.net":name="My Thing" -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=1761:vpass=2 -vf pp=de,crop=688:368:20:56,scale=640:-2   -ffourcc DX50 -o "/home/mikey/MyFile-1.avi"
unlink frameno.avi 2> /dev/null
unlink divx2pass.log  2> /dev/null
mencoder dvd://1 -chapter 10-19 -oac mp3lame -lameopts abr:br=128 -aid 129  -ovc frameno -o frameno.avi
mencoder dvd://1 -chapter 10-19 -sid 0 -vobsubout /home/mikey/MyFile-2 -info srcform="DVD ripped by acidrip.sf.net":name="My Thing" -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=1970:vpass=1 -vf pp=de,crop=688:368:20:56,scale=640:-2   -ffourcc DX50 -o "/dev/null"
mencoder dvd://1 -chapter 10-19 -sid 0 -vobsubout /home/mikey/MyFile-2 -info srcform="DVD ripped by acidrip.sf.net":name="My Thing" -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=1970:vpass=2 -vf pp=de,crop=688:368:20:56,scale=640:-2   -ffourcc DX50 -o "/home/mikey/MyFile-2.avi"
unlink frameno.avi 2> /dev/null
unlink divx2pass.log  2> /dev/null


```

---

### Post by mikeym on 2006-07-28
I have checked and I have seen this method given as a way of doing a 3 pass encode. What is wrong?

---

### Post by mikeym on 2006-07-28
It is obviously copying the audio from the DVD file rather than the fileno.avi file. Do I have to encode the aduio each time I run mencoder?

---

### Post by mikeym on 2006-07-28
I have tried removing the "-fourcc DX50" flag incase it was somehow causing the probplem. I have also tried removing the "-oac copy" flag on the second pass. Neither has fixed the problem. Could this be a problem with my version on mencoder? (MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C))

---

### Post by mikeym on 2006-07-30
For anyone who is interested the mencoder 3 pass encoding technique has been depreciated so it is no longer supported. 

Use 2 pass encoding instead. The output you get should be of a similar quality anyway.

---

