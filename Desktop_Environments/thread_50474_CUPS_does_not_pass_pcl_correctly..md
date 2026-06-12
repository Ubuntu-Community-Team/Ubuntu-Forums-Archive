---
title: "CUPS does not pass pcl correctly."
date: 2005-07-20
forum: Desktop Environments
---

### Post by dmallery on 2005-07-20
I rarely use pcl but for one group of applications.  I have a xerox n17 printer that always worked perfectly with pcl, changing trays and stackers, fonts, etc.

Yesterday, i had to go back and run one of those pcl apps... controlling the envelope feeder on the printer.  The printer simply prints the pcl commands like data on normal paper, ignoring the pcl:

lab64:~/wnmwpa> head pcl.txt
@PJL SET LPARM : PCL FONTNUMBER=8
&a9L10Vhi

director envelopes:

program is direnv... there is a director spreadsheet.
 pclsnd -elP12 -F1 dir_env
.....
(this is just a simple command to print a help file)

I have tried the following:

same results from two different computers (both ubuntu).
swapped the processor board on the printer.

meanwhile, the printer prints all postscript, test pages, browser output, open office, etc.

i tried gtklp.  if i select "raw output" on gtklp, it **takes** the pcl and changes font and point size but there are no "returns" at the end of the line, so the printing goes off the right side.  so the printer's pcl abilities are there!

the printer is set up on CUPS as an hp jetdirect.  it answers on 9100.  it has printed pcl for years using knoppix and predecessors.

the printer's configuration sheet with either processor board is the same (save memory size).  the printer's pcl demo sheet is perfect.

i would be very happy with a pointer!

thanks

dave mallery

---

### Post by dmallery on 2005-08-11
I am replying to myself in hopes of finding a clue.

this problem persists: my xerox n17 which has faithfully printed text with embedded pcl for about three years refuses to do so.  instead, it just prints the pcl out with the text.  

i know that the printer is unchanged.  i have tried several mobos in the printer. same.

today, i changed the printer from deskjet emulation to an ipp printer:

[http://10.42.42.200/ipp](http://10.42.42.200/ipp) instead of 10.42.42.200:9100 (which worked for everything but pcl till today)  sadly, everything is the same...lots of postscript,  no pcl.

i am looking for any documentation on the filters:
(from /var/log/cups/error_log)

I [11/Aug/2005:14:37:22 -0600] Adding start banner page "none" to job 200.
I [11/Aug/2005:14:37:22 -0600] Adding end banner page "none" to job 200.
I [11/Aug/2005:14:37:22 -0600] Job 200 queued on 'DocuPrint-N17' by 'dmallery'.
I [11/Aug/2005:14:37:22 -0600] Started filter /usr/lib/cups/filter/texttops (PID  26020) for job 200.
I [11/Aug/2005:14:37:22 -0600] Started filter /usr/lib/cups/filter/pstops (PID 2 6021) for job 200.
I [11/Aug/2005:14:37:22 -0600] Started filter /usr/lib/cups/filter/foomatic-rip (PID 26022) for job 200.
I [11/Aug/2005:14:37:22 -0600] Started backend /usr/lib/cups/backend/http (PID 2 6023) for job 200.
N [11/Aug/2005:14:37:25 -0600] [Job 200] : Print file accepted - job ID 7.

what is texttops??  why does it call pstops?  

should i look elsewhere?

---

### Post by dmallery on 2005-08-11
so texttops is actually text to postscript.....

so i am filtering my pcl into oblivion.  this is why is sorta works when i use raw mode with the gnome lpr program.

so the driver is doing it... i guess pcl is just so ancient...

---

### Post by aguynamedryan on 2008-07-22
> **dmallery said:**
> 
i tried gtklp.  if i select "raw output" on gtklp, it **takes** the pcl and changes font and point size but there are no "returns" at the end of the line, so the printing goes off the right side.  so the printer's pcl abilities are there!


Just came across a similar problem.  My understanding is that if you are going to print a file with PCL commands embedded in it, you have to use "raw output".

I found that under CUPS's "raw output" the text kept moving off the right-hand side of the page even though the PCL commands were properly interpreted.

The PCL-base print files where just using line feeds (\n) to move down to the next line.  They didn't have carriage returns (\r) to bring them back to the left-hand side of the page.  Once I replaced "\n" with "\r\n", my files printed out correctly.  I'm a little surprised that I have to include carriage returns now, but it does get the job done.

I doubt this will help you three years later, but maybe someone else can use this info.

---

