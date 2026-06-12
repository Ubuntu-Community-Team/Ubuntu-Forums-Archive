---
title: "How do I get to the Printer Settings?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by socceroos on 2006-08-09
Hi all, I am having a problem trying to print a pdf.

Our company has a minolta DI650(PI6500e) printer. We use it for production printing.

It has taken me a while to find the proper drivers for this model of Minolta but I finally did (a ppd file on Minolta's website).

I have installed the printer with the drivers and have been able to successfully print a test page to the Minolta.

BUT, my first REAL test was when I went to print a pdf using some of the DI650's advanced features: the program I am using (Document Viewer) to view the pdf doesn't give me the option to select some advanced settings of the Minolta! It only gives the paper type, orientation and a few other things.

I can see all the advanced settings when I right click on the printer in the System->Printers tool but I cant access them in any other application when I go to print to the Minolta!

Why is this? Is there any way to fix it?

---

### Post by RESmonkey on 2006-08-09
Hmm, wierd, I can look at my settings through system>admin>printing.  Have you added a printer manually or some sort of autodetection?

---

### Post by socceroos on 2006-08-09
I installed the printer using the wizard in System>Administration>Printers.

I originally tried using IPP but it wouldn't print to it. So I used Windows Printer and although it would let me print, it wouldn't let me select any advanced options. Now I am using HP JetDirect and it will print to the Minolta, but again, it won't let me see any advanced settings when I print from an application like OpenOffice or Document Viewer.

---

### Post by socceroos on 2006-08-10
So, does anyone know what is wrong?

---

### Post by shawnrgr on 2006-08-10
advanced printing prefs are global. 

system>administration>printing
right-click printer icon
select properties

in that window you can set things like...

paper size/type/source
page region
printout mode (draft, normal, high, photo...)
resolution, quality, ink type, media type
and so on...

hope this helps

---

### Post by Bonez56 on 2006-08-10
I have a HP printer, and also noticed that I can not change print quality from within a program, but there are further options available in the actual printer preferences in System/Administration/Printing when you right click on the printer and select properties.

For HP printers there is a HP toolbox available that gives far further options, but unfortunately i'm not sure if there is anything like this available for Minolta printers :(

---

### Post by socceroos on 2006-08-10
@shawnrgr

But in applications like OpenOffice the ONLY setting it will give me for the paper size is A4.

But I need A4-R, which is in the advanced settings of the printer driver. When I print something from OpenOffice it doesn't use the "Global Settings" in the Advanced tab of the printer driver and just prints to A4. Is this normal?

---

