---
title: "LibreOffice &lt;&gt; MSFT Office interoperability"
date: 2013-02-04
forum: Desktop Environments
---

### Post by mike acker on 2013-02-04
do we have any means of monitoring the resolution of this issue ?

as things stand Libre Office documents produced in Linux are flagged "corrupted" if you try to open them in MSFT/Office

this seems to affect both the open document format ODT / ODS as well as the new ISO "standards"  ( docx / xlsx ) .

this is a HUGE obstacle to getting folks to adopt Linux/Ubuntu

---

### Post by SeijiSensei on 2013-02-04
I don't see how this is necessarily the fault of the Open/LibreOffice developers.  Don't you think it could just as well be Microsoft's "fault?"  Certainly MS has an interest in claiming that documents produced in its allegedly "open" formats by other non-MS software be tagged as "corrupted."

What if you save in the older MS formats like .doc and .xls?  I haven't used MS Office for quite some time, but I recall those worked fine in the past.  You can configure the free office products to save in those formats by default.

Why don't you ask this question in some Microsoft Office support forums and see what responses you get?  I, for one, would be interested in hearing what they have to say.

I'm waiting to see what happens when Microsoft begins pushing its customers to spend $100-150/seat/year for a [subscription]("http://www.pcmag.com/article2/0,2817,2409821,00.asp") to Office 365.

---

### Post by llanitedave on 2013-02-04
It looks to me that MS flags Libre Office Documents as corrupted when it detects certain app-specific tags in the document's meta-data.  It will offer to "restore" the document, and it does so by removing those tags -- I assume so that it won't be so obvious that they were produced by Libre Office.  I've never noticed any formatting or formula changes in Write or Calc douments that were opened in Worde or Excel, even after they were "restored".

(I've had a heck of a time converting from Impress to PowerPoint in previous versions, though -- not sure if that one's fixed or not.)

---

### Post by mike acker on 2013-02-05
I can only report what I am able to test with the software I have available:

[LIST]
[*]LibreOffice 3.5.4.2 running in Ubuntu 12.04
[*]MSFT Office 2010 14.0 32 bit running on Windows 7.
[/LIST]
notes

[LIST=1]
[*]documents produced on LibreOffice under Windows seem to import into MSFT Office "OK"
[*]documents produced on LibreOffice on Linux are flagged as "corrupt" by MSFT Office.  They offer to "recover" the document -- but in xlsx -- they killl all the formulas and import values only
[*]documents produced on MSFT/Offic e import into LibreOffice OK
[*]documents produced on Libre Office/Linux can be imported intop LibreOffice/Windows OK and then saved,-- after which they will import into MSFT?Office OK
[/LIST]
ISO[INDENT]it is my understanding that MSFT got their office formats adopted by ISO . this being the case they should accept documents formatted IAW ISO standard . if they don't they can be sued .
[/INDENT]this compatibility thing is a HUGE problem in front of Linux and particularly distros like Ubuntu that offer a lower cost -- and more secure -- approach to computing 

for our students in particular -- who always have to watch their costs -- I think Linux is on the doorstep of being 1st choice

unfortunately schools may demand .doc/docx | xls/xlsx format documents .  where LibreOffice offers to produce these formats -- the documents should be acceptable in any venue that asks for these formats

we all know .pdf is a better choice for transmittals but we still have to deal with people the way they are

---

### Post by kurt18947 on 2013-02-05
That makes it look like Libre Office needs the equivalent of FireFox's 'User Agent Switcher' (or whatever it's called).  

"See, MS Office?  This file was produced on a system running Windows.  Really.  Seriously":rolleyes:

---

### Post by cigtoxdoc on 2013-03-29
The key thing is to save as doc, xls, and ppt.  Skip the "x".  Also there is some sort of addin for MS Office 2007 that allows opening/saving in open document formats.

John

---

