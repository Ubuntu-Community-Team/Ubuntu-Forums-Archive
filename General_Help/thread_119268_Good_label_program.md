---
title: "Good label program"
date: 2006-01-19
forum: General Help
---

### Post by tim15856 on 2006-01-19
In Windows, I've always liked the label program built into early versions of EZCD creator. I basically want it to create labels for my CD jewel cases. The things I want it to do; 
1) The ability to print outlines of the label so it can be printed on plain paper.
2) Able to access online music CD database (CDDB) and insert song titles directly into label.
3) Allow me to insert pictures and text and be able to resize and rotate the pictures.
4) Able to create booklet and tray labels.
5) Able to print labels.

I found glabels installed, but it only prints to defined labels like Avery. I also didn't see any options for CD cases. Synaptic also has cdlabelgen which may work, but it doesn't print. Instead it creates a postscript file. Anyone know a program that does everything I want?

---

### Post by MJSOnline on 2006-01-19
Thats a very good question.

I too am looking for the same type of program/package.

Is there a way to configure "wine" to run such a package under Ubuntu?  I was thinking of using my Epson Print CD software.

Thanks in advance.
Matthew

---

### Post by slux on 2006-01-19
I don't know of other options but you can feed the postscript file to a printer either with pretty much any PDF viewer (as they tend to also support postscript which is a superset of PDF really) or just use "lpr print.ps" from the command line.

---

### Post by tim15856 on 2006-01-19
[QUOTE=MJSOnline]Thats a very good question.

I too am looking for the same type of program/package.

Is there a way to configure "wine" to run such a package under Ubuntu?  I was thinking of using my Epson Print CD software.

Thanks in advance.
Matthew[/QUOTE]

I don't have the instructions with me, but I copied some info down that explains how to print on CDs. You need to install an updated driver for the Epson in order to get the CD as an media option to print to. After that, there was some instructions on using Gimp to print to the CD. I'll look for it later.

If I can't find what I need, I may try EZCD label maker under wine and see if I can get it to work.

---

### Post by lysis on 2006-01-19
hey guys, i've READ that once you get the printer hooked up you can open up the picture you'd like to print with GIMP and print directly to the cd.

you may want to look into that more, there is also a printer driver available called gutenprinter which i can NOT figure out how to install for the life of me.

let me know.  i've got an R220 being delivered tomorrow!

---

### Post by MJSOnline on 2006-01-19
Hi tim15856.

Thanks for the info. You say an updated Epson driver for the R300.  Where do I get this from?

Any look on finding the info?
Thanks in advance.
Matthew

Lysis, is the printer driver you call "gutenprinter" the same driver that tim15856 is on about?

Do you both have any ideas?

Thanks again.  Matthew

---

### Post by kosmic on 2006-01-19
Ups, sorry wrong post :)

---

### Post by tim15856 on 2006-01-19
Here's what I copied from Linuxprinting.org. I haven't tried it yet. The updated driver is the gutenprint driver. Even though the R200 is mentioned, the same should apply to the R300.

I picked up this printer specificly to do the cd/dvd printing and thus found
it a rather important feature to get working. Printing of photo's and so on
worked perfectly using the drivers included in debian stable (sarge) through 
CUPS. However, the cd printing required a bit of extra work. First I 
downloaded the latest gutenprint drivers from:
[http://sourceforge.net/project/showfiles.php?group_id=1537&release_id=263385](http://sourceforge.net/project/showfiles.php?group_id=1537&release_id=263385)
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

Edit: See this post for instructions on installing the Gutenprint driver. [http://www.ubuntuforums.org/showthread.php?t=119595](http://www.ubuntuforums.org/showthread.php?t=119595)

---

### Post by MJSOnline on 2006-01-25
How do i go about extracting and building gutenprint drivers once I have downloaded them?

Once thats done, what do I do next??

Anyone?  Many many thanks in advance.
Matthew

---

### Post by tim15856 on 2006-01-25
See the link at the bottom of my last post [http://www.ubuntuforums.org/showthread.php?t=119595](http://www.ubuntuforums.org/showthread.php?t=119595)

---

### Post by MJSOnline on 2006-01-27
Ok.  I did all that, downloading, complieing, etc.  SDtill no CUPS+Gutenprint driver showing on printers.  Anyone got any ideas?  Matthew

---

