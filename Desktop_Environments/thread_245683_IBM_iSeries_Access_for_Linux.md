---
title: "IBM iSeries Access for Linux"
date: 2006-08-28
forum: Desktop Environments
---

### Post by elvisd on 2006-08-28
my previous thread: [http://ubuntuforums.org/showthread.php?t=97066](http://ubuntuforums.org/showthread.php?t=97066)
my gentoo solution: elvisd.blogspot.com

Hi all,

i'm posting another time for the same problem.
I must install IBM's iSeries Access for Linux, on U6.06.

Can someone help me please? Has someone this application working?

I have tried version 5.2.0 (1.10) and 5.4.0 too. 
But always the same error:

5250: [ ERROR ]: NSC0017: Xt Warning: Cannot convert string "-*-lucidatypewriter-medium-r-normal-*-24-*-75-75-m-*" to type FontSet.

this font exists on my pc, checked with xfontsel.
I have tried various possible solutions, using another language id, and so on, but nothing helps.

Can someone help me solve this issue so that after I can write a complete how-to?
Thank you all, folks!

kind regards 

elvisd

---

### Post by elvisd on 2006-09-27
bump.

---

### Post by NetworkGuy on 2006-09-27
I'd be interested if you could get this working.  I've only seen this program ever work in Suse.

---

### Post by n8bounds on 2006-10-26
This may be enough to get you started.  The program is an RPM made for Red Hat derived distros, so you have to make all the weird links yourself.  Let me know if you get anywhere, last time I had this working was months ago and I've since re-installed since then.  Good luck!

[http://www.ubuntuforums.org/showthread.php?t=165337&highlight=iseries](http://www.ubuntuforums.org/showthread.php?t=165337&highlight=iseries)

---

### Post by elvisd on 2006-10-26
Thank you n8bounds for your reply and your thread. I'll uprade to Edgy tomorrow and then i'll your procedure... 
Kind regards

---

### Post by akamadoushi on 2006-11-06
Hi.  I was just wondering if anyone had any more information about this issue.  I've got iSeries Access for Linux working on Unbuntu 6.06 on the server only (thanks to elvisd's previous thread).  When a thin client accesses it via XDMCP or a VNC to GDM server I keep getting a font error.

5250: [ ERROR ]: NSC0017: Xt Warning: Cannot convert string "-*-lucidatypewriter-medium-r-normal-*-24-*-75-75-m-*" to type FontSet.

Any information would be greatly apprecaited.  Thanks.

---

### Post by Allen S. on 2006-11-21
bump
Having the same problem.....

---

### Post by Circus-Killer on 2006-12-06
same problem, and if i cant find a solution by the time i finish downloading opensuse, ill have to switch my folks over to opensuse instead of ubuntu. but i spose anything is better than windows.

ill stick with ubuntu, i dont need iseries, its just my parents who need it and i wanna switch them to linux.

---

### Post by Circus-Killer on 2006-12-07
okay, missioned around a bit. found [this pdf]("http://publib.boulder.ibm.com/infocenter/iseries/v5r4/topic/rzatv/rzatv.pdf").

if you goto the pdf, and check under the "Troubleshoot 5250 emulator" section, you will find a solution to the error message. unfortunetly, im at work, and this is for my home pc, so i havent tested the solution out, but it looks promising.

if you do test it, please post your results. if no one has tested it by the time i get home and tested it, i will post the results.

---

### Post by Circus-Killer on 2006-12-09
alright, i've tried everything i can think of. i give up for the time being. i will just switch my folks over to opensuse for now (ill always stick with ubuntu, and im not the one who needs iseries access).

---

### Post by ColdBeer on 2007-01-04
I found the solution :twisted:, because iSeries Access for linux seems to need the xfs font server](*,) :

```
$ sudo aptitude install xfs
$ sudo gedit /etc/X11/xorg.conf
```

Add, into the Section "Files" (between "Section" and "EndSection" this line:

```
        FontPath        "unix/:7100"
```

restart X (or the system) and try your setup5250 or ibm5250.:D

---

### Post by Circus-Killer on 2007-01-04
thanks for the tip, seems like it could be the solution we are looking for. unfortunetly, im still at work, and will only be able to try this when i get home this evening (if i have the time).

as soon as i have tried out your solution, i will post back my results.
thanks for the help. ;)

---

### Post by n8bounds on 2007-02-25
This one should actualy work:

[http://ubuntuforums.org/showthread.php?t=368894](http://ubuntuforums.org/showthread.php?t=368894)

---

