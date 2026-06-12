---
title: "Printer GDI issues Panasonic kx-mb2000"
date: 2010-10-16
forum: Desktop Environments
---

### Post by TerabyteUK on 2010-10-16
Hi, I bought a linux compatible printer.
However when I try to connect it via usb on 9.04 and try printing a test page, ubuntu claims the test page was printed, but nothing comes out the printer.
I used generic GDI.

Is there a standard way to install a GDI printer (even if it's from the command line?).

In general does anybody know how to get it working.

---

### Post by TerabyteUK on 2010-10-31
bump. Update, good news and bad news.
Bad news:
I have not been able to get the scanner functionality working.
Can anybody help me with this? Simple scan states "no scanner detected"

Good news:
I have been able to install the printer on Ubuntu 10.10, panasonic do provide drivers, but they're hidden on the website. There are 3 required to make the printer work, they are RPM's and needed to be converted to deb installs, other solution is to search for it as a network printer.

---

### Post by sisko on 2010-11-03
Ok, please can you tell me what you did to convert the rpm's.  I try and all I get are errors about the files.  Help!  Thanks!

---

### Post by sisko on 2010-11-08
Bump.

The rpm converter isn't working on these files (at least for me).

---

### Post by Spoutniker on 2010-11-29
I had the same problem and I used alien to convert the .rpm
Here's the link on the french forum :
[http://forum.ubuntu-fr.org/viewtopic.php?id=430179](http://forum.ubuntu-fr.org/viewtopic.php?id=430179)

Have you got a problem to wake up the printer after it puts itself in stand-by mode (after 5 or 15 min)?

---

### Post by colorblue on 2011-04-27
I finally got this working on Ubuntu 64. After much experimentation and help from Alex Kuklin ([http://alexkuklin.livejournal.com/1073809.html](http://alexkuklin.livejournal.com/1073809.html)) here is how I got it working.

1. extract the rpms from [http://www.panasonic.net/pcc/support/fax/common/table/linuxdriver.html](http://www.panasonic.net/pcc/support/fax/common/table/linuxdriver.html)  into a folder. I used alien (if you dont know how to do this google it, there are plenty of instructions out there). 

2. from the libtetra and libjbig folders, copy the files from  <libtetra and libjbig>/usr/lib into /usr/lib32

3. make sure the links are in fact copied as links. I had to recreate mine for some reason. 

4. From the rastertogdi folder (extracted using alien) copy usr/lib/cups/filter/* to /usr/lib/cups/filter  (you need both files)

5. Now we follow Alex's instructions. Get libcupsimage2 for i386 from [http://ftp.us.debian.org/debian/pool/main/c/cups/libcupsimage2_1.4.4-7_i386.deb](http://ftp.us.debian.org/debian/pool/main/c/cups/libcupsimage2_1.4.4-7_i386.deb) and extract the files into another folder (if you dont know how to do this google it, there are plenty of instructions out there).

6. copy libcupsimage.so.2 in  /usr/lib32/

7. restart cups 

8. now install the printer driver system> administration> printer > new printer

9. find the printer and when the list of drivers show up, select the middle radio button, "provide ppd"

10. select the ppd from the rastertogdi folder (extracted with alien above). The ppd is located in <rastertogdi folder>/usr/share/cups/model. Select kx-mb2000 

11. print test page and enjoy.


if you didnt use alien and extracted the rpms using any other method follow the relative paths.

---

### Post by w3#4F%M@§yAKt2 on 2011-05-01
> **colorblue said:**
> I finally got this working on Ubuntu 64. After much experimentation and help from Alex Kuklin ([http://alexkuklin.livejournal.com/1073809.html](http://alexkuklin.livejournal.com/1073809.html)) here is how I got it working.

1. extract the rpms from [http://www.panasonic.net/pcc/support/fax/common/table/linuxdriver.html](http://www.panasonic.net/pcc/support/fax/common/table/linuxdriver.html)  into a folder. I used alien (if you dont know how to do this google it, there are plenty of instructions out there). 

2. from the libtetra and libjbig folders, copy the files from  <libtetra and libjbig>/usr/lib into /usr/lib32

3. make sure the links are in fact copied as links. I had to recreate mine for some reason. 

4. From the rastertogdi folder (extracted using alien) copy usr/lib/cups/filter/* to /usr/lib/cups/filter  (you need both files)

5. Now we follow Alex's instructions. Get libcupsimage2 for i386 from [http://ftp.us.debian.org/debian/pool/main/c/cups/libcupsimage2_1.4.4-7_i386.deb](http://ftp.us.debian.org/debian/pool/main/c/cups/libcupsimage2_1.4.4-7_i386.deb) and extract the files into another folder (if you dont know how to do this google it, there are plenty of instructions out there).

6. copy libcupsimage.so.2 in  /usr/lib32/

7. restart cups 

8. now install the printer driver system> administration> printer > new printer

9. find the printer and when the list of drivers show up, select the middle radio button, "provide ppd"

10. select the ppd from the rastertogdi folder (extracted with alien above). The ppd is located in <rastertogdi folder>/usr/share/cups/model. Select kx-mb2000 

11. print test page and enjoy.


if you didnt use alien and extracted the rpms using any other method follow the relative paths.


I don't seem to be able to convert these packages into debs using alien. It looks like conversion is going on but no .deb files are being generated...   Did you do anything special to convert from .rpm to .deb?

I simply run:
 sudo alien libjbig-1.0.0-1.i386.rpm

help:)

---

### Post by colorblue on 2011-05-10
> **dreamer111 said:**
> I don't seem to be able to convert these packages into debs using alien. It looks like conversion is going on but no .deb files are being generated...   Did you do anything special to convert from .rpm to .deb?

I simply run:
 sudo alien libjbig-1.0.0-1.i386.rpm

help:)
@dreamer111 you are on the right track. just follow the instructions,  step 1 is to extract the files.
 
sudo alien libjbig-1.0.0-1.i386.rpm  >> should create a folder called libjbig-1.0.0-1.

---

### Post by agoncharov on 2011-06-26
Hi folks!

I've just updated from 32bit 10.04 to 32bit 11.04. The way to add KX-MB2000 support you mentioned above worked fine for 10.04. But it doesn't work for 11.04. In particular, there is no chance for CUPS to run /usr/lib/cups/filter/rastertogdi - it immediately crashes (Segmentation Fault). You may see the valgrind's output below:

```
==9224== Memcheck, a memory error detector
==9224== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==9224== Using Valgrind-3.6.1 and LibVEX; rerun with -h for copyright info
==9224== Command: ./rastertogdi
==9224== 
==9224== 
==9224== Process terminating with default action of signal 11 (SIGSEGV)
==9224==  Access not within mapped region at address 0x4
==9224==    at 0x400AE5D: _dl_relocate_object (dl-reloc.c:242)
==9224==    by 0x4002EDF: dl_main (rtld.c:2260)
==9224==    by 0x4013EED: _dl_sysdep_start (dl-sysdep.c:244)
==9224==    by 0x4004A0F: _dl_start (rtld.c:336)
==9224==    by 0x4000856: ??? (in /lib/i386-linux-gnu/ld-2.13.so)
==9224==  If you believe this happened as a result of a stack
==9224==  overflow in your program's main thread (unlikely but
==9224==  possible), you can try to increase the size of the
==9224==  main thread stack using the --main-stacksize= flag.
==9224==  The main thread stack size used in this run was 8388608.
==9224== Jump to the invalid address stated on the next line
==9224==    at 0x32E: ???
==9224==    by 0x40429E7: ???
==9224==    by 0x4002EDF: dl_main (rtld.c:2260)
==9224==    by 0x4013EED: _dl_sysdep_start (dl-sysdep.c:244)
==9224==    by 0x4004A0F: _dl_start (rtld.c:336)
==9224==    by 0x4000856: ??? (in /lib/i386-linux-gnu/ld-2.13.so)
==9224==  Address 0x32e is not stack'd, malloc'd or (recently) free'd
==9224== 
==9224== 
==9224== Process terminating with default action of signal 11 (SIGSEGV)
==9224==  Bad permissions for mapped region at address 0x32E
==9224==    at 0x32E: ???
==9224==    by 0x40429E7: ???
==9224==    by 0x4002EDF: dl_main (rtld.c:2260)
==9224==    by 0x4013EED: _dl_sysdep_start (dl-sysdep.c:244)
==9224==    by 0x4004A0F: _dl_start (rtld.c:336)
==9224==    by 0x4000856: ??? (in /lib/i386-linux-gnu/ld-2.13.so)
==9224== 
==9224== HEAP SUMMARY:
==9224==     in use at exit: 0 bytes in 0 blocks
==9224==   total heap usage: 0 allocs, 0 frees, 0 bytes allocated
==9224== 
==9224== All heap blocks were freed -- no leaks are possible
==9224== 
==9224== For counts of detected and suppressed errors, rerun with: -v
==9224== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 47 from 5)

```So.. is there any chance for me to return my printer back to the working state? 

Thanks, guys

---

### Post by tommpogg on 2011-10-11
The solution proposed by "colorblue" worked for me.

Thank you

---

### Post by stephanos21 on 2012-02-17
I followed colorblue's guide and the I am not able to print :(

As soon as I try to print something I have a message saying stopped, and I don't know why. If I open the system settings and go to the printers, I get that:
Printer status: Idle : Processing page 1...
and it stays like that forever.

I am using Kubuntu 11.10

---

### Post by tommpogg on 2012-02-20
Hi,

I suggest to take a look to these two threads:
- [http://ubuntuforums.org/showthread.php?t=1870324](http://ubuntuforums.org/showthread.php?t=1870324): it explains why it is so hard to use with a Panasonic printer
- [http://ubuntuforums.org/showthread.php?t=1482510&page=2](http://ubuntuforums.org/showthread.php?t=1482510&page=2): it gives a alternative solution.

Hope it helps.

---

### Post by m420n on 2012-06-26
Hi!

Seems like I cannot start new threads as of now but I think I have a solution for the not so intensive support from Panasonic itself and/or the missing support for Panasonic laser printers from CUPS. 

I already could print with the 32 Bit Edition after installing the driver provided by Panasonic which includes a ppd-file named 'L_Panasonic-MB2000-gdi.ppd'. Under 64 Bit the driver will not install and complain about the wrong architecture.

I have a KX-MB2061 and Ubuntu 12.04 64 Bit Edition. Here is what I did to get that thing to work:

1. downloaded Panasonic driver from their website -> extracted it to a folder
2. copied                            L_H0JDJCZAZ.so.1.0 to /usr/lib32/

3. googled for and downloaded *                      libjbig-1.0.0-1.i386*      + *libtetra-1.0.0-2.i386*
4. extracted these two to separate folders
5. copied the everything to the matching folders in /usr/lib/ and /usr/lib32/ (I was not shure so I copied them to both locations)

6. googled for *rastertogdi-1.0.1-9.i386,*      downloaded it as rpm 
7. extracted it and got a folder usr with two folders in it
8. then copied ../usr/lib/cups/filter/  to  /usr/lib/cups/filter/ and /usr/lib32/cups/filter/
9. also copied ../     usr/share/cups/model (files: kxmb****.ppd) to /usr/share/cups/model
 
10. downloaded libcupsimage2 (i386) -> extracted to folder and copied to /usr/lib32/

12. opened 127.0.0.1 in web browser
13. there chose 'Add Printer' (maybe you want to disable your firewall here, I did)
14. my printer was shown as a recognized network printer (KX-MB2060) -> I  chose that
15. next page I had two vendor entries '*Panasonic*' and                            '*Panasonic Systems Network Co., Ltd.*' -> I chose the second one because only that will present the correct ppd-file (without 'gdi' in its name) in the next step
 16. in the following step I selected                            '*Panasonic KX-MB2000 Series, 1.0.1 (...)*  ' as model
17. now I was able to successfully print a test page :-)

I do not really know, if all these steps are really necessary but this worked for me and I do not have the time to test all the steps for their necessitiy.

This thread got me going in the right direction so thx for the help,  and I hope that others get their faster than me (this would be under 2 days) with this addition.

---

### Post by oldos2er on 2012-06-26
Old thread closed.

---

