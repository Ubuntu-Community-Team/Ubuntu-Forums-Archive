---
title: "how to print"
date: 2005-05-17
forum: Desktop Environments
---

### Post by wilhelm on 2005-05-17
hello folks,

i have ubuntu minimal installed on my machine as per instruction from the "ubuntu mini-ram howto"

i have aslo been able to install my hp colorlaserjet 2550 which connected to the network that i am on, now this is a network printer ( not connected directly to any pc)
 i use the hp 2550 color lasejet postscript drivers, with the jetdirect as the connect and socket://192.168.10.11:9100

but i want to now how do i print from any text editor, command line

i was able to get the pinter to print the cups test page...

but what other commands would be used to print a postscript file ?

any help in this area, or pointer to a recent/detailed howto would be appreciated

--pf--

---

### Post by dave9191 on 2005-05-17
Well if you have the printer setup on the computer, then you can print from apps using the print command and from the command line using the lpr command. 

Dave

---

### Post by wilhelm on 2005-05-17
that is just it ...it doen't work

i don't have the lpq command to check the quee of the printer nor do i have the lpr command to print from CL, which btw is the same command thunderbird and mozilla wants to use to print..

any other suggestions?

---

### Post by dave9191 on 2005-05-17
I though that lpr and lpq came as standard cause I didnt install them and i have them. Try 

sudo apt-get install lpr lpq

Dave

---

### Post by wilhelm on 2005-05-18
thanks mate...
i got that lpr installed , gave me also lpq
i thought it would come in another package...
now i will check what i can get sorted out...

---

### Post by dave9191 on 2005-05-18
Now that you got those, I hope you can sort the printing out :) Good luck.

---

### Post by wilhelm on 2005-05-18
hi

well i struggled some more , asked a couple more Q's on another mailing  list and here i am ....PRINTING!!!...


lol

well what i did was removed the lpr package because i still couldn't print, from another suggestion i install cupsys-bsd which also provides the lpr and lpq and which is more compatible with cupsys...
so after i installed that i just had to set the printer again to accept jobs and now i can print....

thanks for all the help dave...

---

### Post by dave9191 on 2005-05-18
Im still supprised that you didnt have lpr and lpq with a standard install. You did do a standard install right ?

---

### Post by lorap on 2005-05-18
hi
no, he did a partial installation.
probably in that kind of installation lpr isn't included what's very strange...

---

### Post by dave9191 on 2005-05-18
Argh, my fault. I missed the minimal install part. My bad.

---

### Post by wilhelm on 2005-05-19
good question would be did anyone else get the same when they did the mini install? if so than i suggest updating the howto :) if not, i must have missed something somewhere, although i did it step by step in the same order

---

