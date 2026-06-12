---
title: "Installation SUCESS on DELL DIMENSION XPS T500"
date: 2008-02-06
forum: Dell  Ubuntu Support
---

### Post by pmshirey on 2008-02-06
I had a total success on this system. It was designed for Windows 98 and was given to me by a friend. I popped the alternate disk in and away I went. The only reconfiguration of the interior I had to do was put a network card in because these dells are completely dial up.:lolflag:

---

### Post by joebookpro on 2008-02-11
I have the same system and I cannot get any of the live cds to run or the install disks. I would like to install Edubuntu on this system. How did you get the system to boot from a CD? Please help.

---

### Post by myusername on 2008-02-12
^ check your bios

i have the t550 and it worked perfectly but i also upgraded the ram to 512

---

### Post by joebookpro on 2008-02-12
I have checked the bios, it is set to boot from the CD first and it still just boots into windows. I have tried several install/live CDs and nothing seems to work. I am lost on how to get this working. I know that the discs are burned correctly, but still no luck.

---

### Post by zardrube on 2008-02-28
I am guessing you have done this, but check the age of the BIOS. The optional BIOS Dell recommends is A10 or A11 (some kind of A10 derivative) for these 1999 machines. Gutsy was going CRAAAAAZY trying to load on my pre-2000 BIOS. I was getting Squashfs SR0 errors and Sb_bread failed errors over and over. Frankly I have no idea what either of them means. And hopefully I will never need to find out.

I finally found the A10 BIOS (sadly I can't find where on their site) and then an A3 BIOS from 2006 which wouldn't load due to an SMBIOS table error. This is only relevant since the A10 and its cousin A11 BIOS are from 2000.

I have now loaded the live CD and am currently installing Ubuntu on the Dell. I might be light on memory for Gutsy Gibbon, but that can be fixed. 

Here is a link that should bring you to the Dell location where A11 resides: 

[http://support.dell.com/support/downloads/driverslist.aspx?os=NAA&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=DIM_PNT_P03_XPS_T___&hidos=DOS&hidlang=en](http://support.dell.com/support/downloads/driverslist.aspx?os=NAA&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=DIM_PNT_P03_XPS_T___&hidos=DOS&hidlang=en)

I will leave a follow up post with the Gutsy Gibbon machine.

Cheers,

B

---

### Post by zardrube on 2008-02-29
Now I have Jean Luc Ponty playing :guitar: on the Awesome sound of the Gutsy Gibbon I am writing on in my office.

This indeed can work, but it will take patience. Have fun. I told you I'd let you know when it worked. try the BIOS upgrade and give your old PC new life.

B

---

### Post by gonesolo on 2008-02-29
Here is the link to the latest bios for that system from the Dell support site.

[http://support.dell.com/support/downloads/format.aspx?c=us&l=en&s=gen&deviceid=308&libid=1&releaseid=R22940&vercnt=9&formatcnt=0&SystemID=DIM_PNT_P03_XPS_T___&servicetag=&os=W98&osl=en&catid=-1&impid=-1](http://support.dell.com/support/downloads/format.aspx?c=us&l=en&s=gen&deviceid=308&libid=1&releaseid=R22940&vercnt=9&formatcnt=0&SystemID=DIM_PNT_P03_XPS_T___&servicetag=&os=W98&osl=en&catid=-1&impid=-1)

It's vesion A11.

If you REALLY want the A10 here is the link to that.

[http://support.dell.com/support/downloads/format.aspx?c=us&l=en&s=gen&SystemID=DIM_PNT_P03_XPS_T___&servicetag=&os=W98&osl=en&deviceid=308&libid=1&catid=-1&impid=-1&typecnt=0&vercnt=9&releaseid=R17425](http://support.dell.com/support/downloads/format.aspx?c=us&l=en&s=gen&SystemID=DIM_PNT_P03_XPS_T___&servicetag=&os=W98&osl=en&deviceid=308&libid=1&catid=-1&impid=-1&typecnt=0&vercnt=9&releaseid=R17425)

Happy upgrading :)

---

### Post by joebookpro on 2008-02-29
So, I gave up on the XPS T500 because I recently aquired a Compaq PIII 1000 Mghz. Thanks to everyone who tried to help me. The Compaq is currently running Edubuntu very well, my kids love all of the fun games.

---

