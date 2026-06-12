---
title: "How to Print to PDF"
date: 2009-03-22
forum: General Help
---

### Post by Kissell on 2009-03-22
I really need the ability to create PDF documents via a system pdf printer.  Can someone help me please!?

I have installed cups-pdf > sudo apt-get install cups-pdf

but even though it is in the repositories, it doesn't work.

When I try to print I get a failure until I change permissions on a file > sudo chmod 755 /usr/lib/cups/backend/cups-pdf but after setting the permissions so my user can read the file, it appears to print correctly, but no file is created.  

I have followed many threads like this [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/295536]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/295536") but they are just other people verifying they have the problem too.  I haven't been able to find a solution anywhere.  

I created the ~/PDF folder for the output files before installing cups-pdf and still nothing.  I can't get it to work in Ibex or Jaunty.  If someone could help that'd be great.  I don't care about using cups-pdf, I just care about printing to PDF, so if someone knows of another app that I can install to accomplish this, that'll work for me.

---

### Post by DeMus on 2009-03-22
> **Kissell said:**
> I really need the ability to create PDF documents via a system pdf printer.  Can someone help me please!?

I have installed cups-pdf 

but even though it is in the repositories, it doesn't work.

When I try to print I get a failure until I change permissions on a file  but after setting the permissions so my user can read the file, it appears to print correctly, but no file is created.  

I have followed many threads like this [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/295536]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/295536") but they are just other people verifying they have the problem too.  I haven't been able to find a solution anywhere.  

I created the ~/PDF folder for the output files before installing cups-pdf and still nothing.  I can't get it to work in Ibex or Jaunty.  If someone could help that'd be great.  I don't care about using cups-pdf, I just care about printing to PDF, so if someone knows of another app that I can install to accomplish this, that'll work for me.

Didn't you get a PDF printer with the standard installation of Ubuntu? I think I did, cause I can not imagine I installed one and I do have one.
Also, if you work in OpenOffice, you don't have to print to a PDF printer, you can export your files as PDF, which gives you a high quality output.

---

### Post by Kissell on 2009-03-22
There was no PDF printer installed by default, I just reinstalled.

Exporting to PDF is alright for open office, but most of the time I'm wanting to print to PDF from firefox.

---

### Post by sgosnell on 2009-03-22
Have you tried the steps in [this tutorial](http://www.arsgeek.com/2007/05/17/5-steps-to-create-a-pdf-printer-print-to-pdf-in-ubuntu/)?  It was one of the first sites that turned up in a Google search.

---

### Post by Rallg on 2009-03-22
If you think that you have the right stuff installed to get a PDF printout, but it doesn't work, then try this: Make a folder named PDF in your home directory. Then try a print. See if the result is in the PDF folder.

Apparently cups-pdf wants it that way, but doesn't do it automatically.

---

### Post by dwightparker on 2009-03-22
Thanks...creating the folder made it work...

---

### Post by sgosnell on 2009-03-22
I just installed cups-pdf, and it automagically installed a PDF printer, and made the /home/user/PDF directory.  Printing to PDF puts the output .pdf file in that directory.  I didn't need to change any permissions or anything, it just worked out of the box.

---

### Post by Kissell on 2009-03-22
I had already tried to manually create the ~/PDF folder, but it still doesn't work after creating the folder.

sgosnell: I've tried the steps in that tutorial.  I can get a printer created, but it just doesn't output a file anywhere after printing.

This is a fresh Ibex install I'm using, just installed it this morning.

---

### Post by Kissell on 2009-03-22
> **sgosnell said:**
> I just installed cups-pdf, and it automagically installed a PDF printer, and made the /home/user/PDF directory.  Printing to PDF puts the output .pdf file in that directory.  I didn't need to change any permissions or anything, it just worked out of the box.

I've reinstalled Ubuntu several times, and cups-pdf never works like that for me.  In fact, it never works at all anymore.  It worked fine in Hardy, but I really don't want to downgrade that far.

---

### Post by 3Miro on 2009-03-22
So if you try to do print in firefox, then you select print to file, then there is no option next to the print to file to say PDF?

If you run everything from a Terminal do you get any errors?

---

### Post by sgosnell on 2009-03-22
3Miro, there is no Print To File dialog, you select a printer, which is a PDF virtual printer.  It 'prints' to a file in ~/PDF.

Kissell, I'm afraid I have no help for you.  I'm on Jaunty, and it worked out of the box for me.  I don't want to downgrade to Intrepid.  I have no idea why it won't work for you, sorry.

---

### Post by Kissell on 2009-03-23
I installed jaunty and can't get it to work there either.  There is a "print to file" that doesn't work, along with the PDF printer...  I didn't try to use the print to file before I installed cups-pdf, but neither of them work for me in jaunty either.

---

