---
title: "&quot;Failed To Print Document, Too Many Failed Attempts&quot;"
date: 2009-03-30
forum: General Help
---

### Post by JohnnyReb on 2009-03-30
Ok, I get this error when printing a PDF from Document Viewer (Evince). It works fine if I print all pages but, if I only print certain pages, I get this error. I can eventually get it to print by retrying. It may take 1 or 100 retries but it will go eventually. I'm printing to an HP Laserjet 4000 with a Jet Direct Card via TCP/IP. Any help would be greatly appreciated. 

Thanks
David

---

### Post by Ian Sinclair on 2009-04-01
Two weeks ago I could print a PDF document (HP Color Laserjet 2600n). Now, since an update of CUPS I get the "Too many failed attempts" message. Any way of reversing the update and getting back the use of my printer?

---

### Post by Ian Sinclair on 2009-04-01
I think now it might be an Evince problem - I can print from Gnome ePDFviewer (but with a poor-looking font and some spacing errors).

---

### Post by Ian Sinclair on 2009-04-01
Cracked it!  I removed Evince, rebooted and reinstalled Evince. Now printing (and smiling) again!

---

### Post by Ian Sinclair on 2009-04-01
Spoke (and wrote) too soon. I printed out a complete PDF document with no problems, but when I tried to print another one I got the familiar "Too many failed attempts" report once again. Can't figure out why - the machine had not been turned off between these efforts, but somehow it reverted.

---

### Post by skliarie on 2009-04-12
I have submitted a bug report on the issue, you are welcome to contribute to it:
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/359975]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/359975")

---

### Post by nitebriar on 2009-04-22
I was having the same issue, the instructions on the following link worked:

[http://brainextender.blogspot.com/2009/01/ubuntu-intrepid-too-many-failed.html](http://brainextender.blogspot.com/2009/01/ubuntu-intrepid-too-many-failed.html)

I was able to print just one page from evince.

---

### Post by Ian Sinclair on 2009-04-23
Didn't work for me - the lines mentioned in the conf file did not exist.

---

### Post by Lucretia on 2009-06-14
I have had very similar problems. I used to be able to print just fine, and then suddenly couldn't. I am still running 8.10.

Until very recently, I could print to most printers via CUPS, but had trouble with printing to a Windows printer via samba. I could print from OO and test pages, but nothing else. Now, I can't print at all. I keep downloading all the printing related updates, but they never help.

I never know whether my printing problems are because of me or my department's network settings! :(

The samba printer briefly worked when I first set it up, but then a day later I couldn't print anymore.

---

### Post by HermanAB on 2009-06-14
I have seen this on a totally different Linux system (Mandriva 2009).  I haven't been able to figure out whether this is a printer driver, CUPS or USB problem.  Pretty damn annoying.  

My workaround is to turn the printer off and on, which forces a reset all the way up the protocol stack.

---

### Post by Lucretia on 2009-06-14
Okay, to expand on what I said before... I had the wrong IP address for the printer, so now that's fixed. I can print test pages and OO again and also Matlab, but anything else gives an error of "Too many failed attempts" or just does nothing (firefox).

The printer is attached to an XP machine. I set it up in Administration->Printing->Windows Printer via SAMBA.

I tried copying the printer as was suggested in various places, and I was able to print something from Image Viewer. However, when I closed Image Viewer and opened another thing to print, the printers were no longer listed! All I have is print to file and lpr. Same goes for the Gimp. However, all the printers still appear in OO and firefox. Haven't checked anything else. I was also able to print from firefox once, but then not again. No error and the job doesn't even appear in the print queue.

Some discussion on the bug reports suggests that this is a gtk problem.

---

### Post by Elwro on 2009-06-15
I also get this error. Printing every document 1 page at the time is quickly becoming frustrating! I first noticed the problems after switching to 9.04. The cups error.log ends with "cupsdReadClient: 8 IPP Read Error!", so the iinstructions from [http://brainextender.blogspot.com/2009/01/ubuntu-intrepid-too-many-failed.html](http://brainextender.blogspot.com/2009/01/ubuntu-intrepid-too-many-failed.html) won't help in this case: this is not an authorisation issue. 

Any pointers?

---

### Post by NickD-NLUG on 2009-06-27
> **Elwro said:**
> I also get this error. Printing every document 1 page at the time is quickly becoming frustrating! I first noticed the problems after switching to 9.04. The cups error.log ends with "cupsdReadClient: 8 IPP Read Error!", so the iinstructions from [http://brainextender.blogspot.com/2009/01/ubuntu-intrepid-too-many-failed.html](http://brainextender.blogspot.com/2009/01/ubuntu-intrepid-too-many-failed.html) won't help in this case: this is not an authorisation issue. 

Any pointers?

Sorry, no pointers, just wanted to say I've started to seen the same problem since the upgrade to 9.04.

Did you get anywhere in trying to diagnose this?

---

### Post by Duncan J Murray on 2009-07-09
Me too, I get a similar error, with both the document viewer and scribus, using a Canon IP2500 printer.  It seems to particularly affect large files, and restarting the printer seems to help on occasion.

Duncan.

---

### Post by nelfer on 2009-07-09
I believe this is evince. I wasn't able to print multiple copies of a PDF. Then printing one by one worked, but then just printing one document, one copy, didn't work anymore. Then it seemed like only small PDFs (1 to 3 pages) could print properly.

So I downloaded ePDFViewer and printed from there (I'm using Jaunty). ePDFViewer printed with no problem and as many copies as I wanted, no matter the size of the PDF.

That's why I don't think is CUPS or the Printer. I went to CUPS page ([http://localhost:631](http://localhost:631)) and the "Failed attempts" didn't even hit CUPS, they didn't appear as jobs. So I'm imagining that evince is sending something wrong to CUPS and since CUPS doesn't answer, it considers it a "failed attempt".

---

### Post by oxf on 2009-07-17
Just to say I'm getting this problem as well. I found no mention of it in CUP's, that said I'm not really sure what I'm looking for and am looking here for advice :)

I'm getting it with PDF's and firefox. I haven't noticed it in Open Office yet but these are usually only one page docs where a s the others, particularly the PDF's are multiple page docs.

(initially in Firefox I wondered if it might be due to the large college WiFi network I usually  log onto but after thiking about that for  a while have discounted that now)

---

### Post by Duncan J Murray on 2009-07-26
> **nelfer said:**
> 
So I downloaded ePDFViewer and printed from there (I'm using Jaunty). ePDFViewer printed with no problem and as many copies as I wanted, no matter the size of the PDF.


Thank you nelfer, I will give ePDFviewer a try.

All best,
Duncan.

---

### Post by giddyman on 2009-07-29
Adobe Reader 9 will solve the problems about PDF files.

---

### Post by rpi+ on 2009-08-15
I had the same problem and I found the solution in the german ubuntuusers.de forum:
Here is the link:
[http://forum.ubuntuusers.de/topic/drucken-schlaegt-oftmals-mit-dieser-meldung-f/?highlight=cups#post-2043588](http://forum.ubuntuusers.de/topic/drucken-schlaegt-oftmals-mit-dieser-meldung-f/?highlight=cups#post-2043588)

In the forum user **deMaumont** (thanks again!) published a solution, here i try a translation of the necessary three steps:

1. sudo /etc/init.d/cups stop
2. edit as root the file /etc/cups/printers.conf, comment the following line so thats it looks like:

   #AuthInfoRequired username,password
3. sudo /etc/init.d/cups start

In my case obviously this was not a problem of evince!

rpi.

---

### Post by robstel on 2009-08-15
Thank you rpi (and Dankeschön to deMaumont) !!! This bug was really annoying me, as it affected Firefox (which just silently failed to print) as well as Adobe Reader & Evince.

---

### Post by enathanson on 2009-09-02
As all who have tried it undoubtedly know now, commenting out the Authorization line only works the first time, because the line is then automatically rewritten (uncommented again, of course).  At least I've figured out why it works once after doing some back flips, but not the second time.

---

### Post by jonlowe on 2009-09-03
One thing that works for me as a temporary workaround is to hit the Print Preview button in the print dialog, and then print from there.  Doesn't take much longer.

---

### Post by khurtsiya on 2009-09-10
Any other solutions as of yet?

I tried to print whole PDF (in Evince) - this error appeared.

Then I tried to print 1-2 pages - OK.

Then 3-4 pages - failed!

---

### Post by pharm on 2009-09-27
hi all
im suffring long time from this bug. printing from firefox/evince does not work. giving me a random error (faild to authenticate, too many failed attemps...)

the only way i came along is to print whatever you want to print to a file. (print to file :P) save where you can find it easy. open shell and cd to saveplace of the pdf-file. then type:

```
lpr file.pdf
```change file.pdf to your filename.
throu lpr *.pdf and *.ps files are printable.

now i'm wondering why i can't find this workaround anywhere? it works everytime.
moreover why don't the developers of the gtk engine temporarly save the printouput into a file use lpr to print?

greetz

---

### Post by nuir on 2009-09-29
> 1. sudo /etc/init.d/cups stop
2. edit as root the file /etc/cups/printers.conf, comment the following line so thats it looks like:

#AuthInfoRequired username,password
3. sudo /etc/init.d/cups start

My .conf file doesn't even have that line :confused: Any other ideas? I print a lot of .pdf files so this is a very annoying bug.

---

### Post by kgarbutt on 2009-11-13
When Document Viewer won't print my pdfs, I print them within OpenOffice (but to print them in OO you need to install their pdfimport tool).

---

### Post by lazylew on 2009-12-27
> **jonlowe said:**
> One thing that works for me as a temporary workaround is to hit the Print Preview button in the print dialog, and then print from there.  Doesn't take much longer.Good workaround, also because there still is the option of printing the whole PDF or just certain pages.

---

### Post by OrionXIII on 2010-01-22
Great workaround!! My 39 page PDF prints just fine if I do it that way...Thanks!

Orion

---

### Post by tjvigil66 on 2010-04-28
I was on my way to uninstalling/reinstalling Evince as someone else posted earlier as a fix.  Instead, I found ePDFviewer.  I took a chance and it just worked... and worked and worked!

"...in the lines of Evince, but without using the Gnome libraries."

[edit]
I found one problem.  I have a file that was created in Inkscape which included an image that has transparency to 20% and saved to PDF.  The document shows up fine in ePDFviewer's window, but the image doesn't show up at all when printed.  If I actually modify the PNG image in GIMP to be semi-transparent and use that image inside Inkscape, then the resulting PDF prints as expected.

---

