---
title: "Epson R2200 Printer (prints on cds)"
date: 2006-01-17
forum: General Help
---

### Post by lysis on 2006-01-17
i'm considering getting the epson r2200 printer so i can print directly onto discs instead of writing on them with markers (i've already got printable media)

will this printer work in ubuntu?     what program can i use to make the label and send it to the printer?

---

### Post by MJSOnline on 2006-01-17
Hi lysis.

I too have a Epson R300, same idea as the R220.

I too am on the look out for an CD Labeling package, as I did use Epson Print CD under Windows.

Take a look at System > Admin > Synaptic Package Manager > Do a seach for cdlabel and take a look at cdlabelgen.

I am hoping it does the same job, almost as Print CD did.

Any luck, let us know.
Matthew

---

### Post by lysis on 2006-01-17
i've not yet bought the r2200.  i did want to make sure that i'll be able to get the job done with ubuntu or else i was considering just waiting until a package was available.

i've already got cd JPEGs or other pictures available that will go onto the disc, i just need to be sure that cdlabelgen can do it!!!

i'm installing it now, and when i get home i'll check it out (i'm remote logged in to install it through command)


thanks!

---

### Post by lysis on 2006-01-17
i've not yet bought the r2200.  i did want to make sure that i'll be able to get the job done with ubuntu or else i was considering just waiting until a package was available.

i've already got cd JPEGs or other pictures available that will go onto the disc, i just need to be sure that cdlabelgen can do it!!!

i'm installing it now, and when i get home i'll check it out (i'm remote logged in to install it through command)


thanks!

---

### Post by MJSOnline on 2006-01-17
Ok. That good.  Let me know how it goes. Matthew

---

### Post by lysis on 2006-01-17
both cdlabelgen and kcdlabel are for the books and the back papers and stuff.

i need the disc itself.

---

### Post by MJSOnline on 2006-01-18
Damm!!

Can anyone name a package or a way round this?

Many thanks in advance.
Matthew

---

### Post by lysis on 2006-01-21
well i tried the "you can do it with gimp" theory and i can't. i don't have a source or a paper type of "compact disc" or anything of the like.

i tried getting gutenprint driver working but i received this error

```
make[3]: Entering directory `/home/lysis/gutenprint-5.0.0-rc1/src/gimp2'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/lysis/gutenprint-5.0.0-rc1/src/gimp2'
Making all in cups
make[3]: Entering directory `/home/lysis/gutenprint-5.0.0-rc1/src/cups'
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2   -o epson  epson.o -lcupsimage -ltiff -ljpeg -lpng -lm -lz -lcups -lnsl
gcc -g -O2 -o epson epson.o  -lcupsimage /usr/lib/libtiff.so -lc /usr/lib/libjpeg.so -lpng -lm -lz -lcups -lnsl
/usr/bin/ld: cannot find -lcupsimage
collect2: ld returned 1 exit status
make[3]: *** [epson] Error 1
make[3]: Leaving directory `/home/lysis/gutenprint-5.0.0-rc1/src/cups'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/lysis/gutenprint-5.0.0-rc1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lysis/gutenprint-5.0.0-rc1'
make: *** [all] Error 2

```

now lcupsimage does NOT exist, but i DO have libcupsimage2 installed on my system.   


what can i do to get this working???!!!???

---

### Post by lysis on 2006-01-24
any suggestions for being able to print directly to my cd tray?

---

### Post by lysis on 2006-01-25
i've tried the gutenprint driver (several versions) and it too will not install due to an error. can anybody assist?

---

### Post by tim15856 on 2006-01-25
Here's what I copied from Linuxprinting.org. I haven't tried it yet. The updated driver is the gutenprint driver. Even though the R200 is mentioned, the same should apply to the R300 or your R2200

I picked up this printer specificly to do the cd/dvd printing and thus found
it a rather important feature to get working. Printing of photo's and so on
worked perfectly using the drivers included in debian stable (sarge) through 
CUPS. However, the cd printing required a bit of extra work. First I 
downloaded the latest gutenprint drivers from:
[http://sourceforge.net/project/showf...ease_id=263385](http://sourceforge.net/project/showf...ease_id=263385)
At the time this was gutenprint-5.0.0-beta4. I extracted the files, and built
them from source without any issues. Check the debian/control file for
required packages need to compile in debian. After doing the ./configure;
make; make install I had available in cups the driver "EPSON Stylus Photo 
R200 - CUPS+Gutenprint v5.0.0-beta4 (en)" which I selected and used. This 
driver provides a media source of "Print to CD", and a paper size of 
"CD - 5 inch" which allows the cd/dvd tray to work. Using the gimp to 
create the cd/dvd image works very well and the gimp 2.2.6 at least includes
a template for CD cover which is the proper size, and also gives all the 
printer media source/paper size options right in the gimp so you don't need 
to specify them as defaults in CUPS itself. 

One other thing to note, is to make sure you leave about 6" of space behind
the printer for the cd tray to stick out, otherwise it will just try to load
the cdtray and then pop back out and error.

The procedure for create and print your Cds are:

1. In the GIMP, go to "File" --> "New" 
2. There, you have to choose "Template" --> "CD Cover 300DPI"
3. You can use your imagination and your artist skills for create your CD Cover
4. When you are prepared to print...
5. Go to "File" --> Print
6. Now, Please you "have" to choose "Printer Configuration"
7. In "Printer Make" you have to Choose "Epson" --> Epson Stylus Photo R200 --> Accept (ok)
8. And the parameters for the printer now, are available. In Source Media You have to choose "Print To CD"
9. You can change other parameters and now you will print yours Covers CD!

See this post for instructions on installing the Gutenprint driver. [http://www.ubuntuforums.org/showthread.php?t=119595](http://www.ubuntuforums.org/showthread.php?t=119595)

---

### Post by lysis on 2006-01-26
as mentioned; i can't install the gutenprint drivers because they tell me that something i have is missing. they have it named wrong.

---

### Post by paran on 2006-08-21
I have solved to prints on cds by Epson Stylus Photo R300. 8) 

USE THAT HELP ON YOUR OWN RISK.

(I hopely write understandable english).
0. READ YOUR EPSON GUIDE:"HOW TO PRINT MEDIA WITHOUT COMPUTER" ;)
1. You need USB-memory or one R300 copatible memorycard, which is formatted to fat.(win32 fat - I beleave). (8 Megabyte is enough)
2. delete all files from USB-memory (or memorycard).
3. clear recycle bin.
4. change cd-picturefile format to jpegs and name it to 1.jpg.
5. put USB-memory or memorycard to your ubuntu-computer.
6. copy 1.jpg file into your empty USB-memory or memorycard.
7. unmount your USB-memory or memorycard.
8. take out of your computer your USB-memory or memorycard.
9. now, you can turn off your Ubuntu-computer, if you like.
10. turn on your Epson
11. put printable cd to Epson CD-tray
12. put CD-tray to ready to print (locate CD-tray's and Epson's arrows)
13. put USB-memory or memorycard to your Epson.
14. choose No.1 picture by keys of Epson. (you can't shoose any other, because your USB-memory or memorycard was empty before you copy 1.jpg).
15. press OK-key from Epson.
16. press <I>-key from Epson. (<I>-key == print-key)
17. Now, epson should start to print to your CD.

---

