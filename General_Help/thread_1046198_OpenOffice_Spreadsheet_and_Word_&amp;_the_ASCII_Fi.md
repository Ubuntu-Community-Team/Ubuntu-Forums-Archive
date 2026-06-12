---
title: "OpenOffice Spreadsheet and Word &amp; the ASCII Filter Options"
date: 2009-01-21
forum: General Help
---

### Post by LindaLou on 2009-01-21
I am using the latest versions of OpenOffice.  Ny web browser is FireFox 3 (updated)and am using the Unbuntu 64bit updated. Yesterday a co worker was attempting to modify a saved document that was in PDF format. Not knowing that this was not possible, attempts to succeed have caused the following:

1. Clicking on any saved PDF documents produced a popup window for ASCII Filter Options.  The language wasn't changed - remains in English - but my coworker thinks that he changed the code.  It is now at Unicode t8 I think.  I say "I think" because now, I am unable to open the document by double clicking, which would give me the popup ASCII window. Now I have to select the pdf document, right click and select "Open With "Document Viewer" ".  This works fine.  

2. Clicking on any Oo Word documents produces nothing. Right clicking and selecting "Open With Oo.org Word Processor", produces nothing.

3. Clicking on any Oo Spreadsheet documents produces nothing.  Right clicking and sleecting "Open with Oo.org SpreadSheet" produces nothing

4.  Going to Applications > Office > Oo Word Processor or Spreadsheet and highlighting and clicking on either program,  produces nothing.  

5. If I want to open a Oo Word document of Oo Spreadsheet from an email, nothing happens.  If I click on "Save" the document is saved to my desktop and I am able to open ONLY PDF formatted documents.  I cannot open Oo Spreadsheets of Oo Word documents

I have a second user on this PC and have applied all of the above with complete success (i.e. I have Oo software in Applications, I can save or open any and all types of documents, etc.). 

Without knowing exactly what was attempted by my co worker, the above information is all that I have.  I would greatly appreciate assistance in resolving this matter.  The PC is my office computer and I am sure you can see the disruption this has caused me.  Looking forward to some resolve here.

---

### Post by LindaLou on 2009-01-21
I found this post and am wondering if it is still a valid work around for my issue with Open Office:

[http://ubuntuforums.org/showthread.php?t=251868&highlight=open+office+ascii](http://ubuntuforums.org/showthread.php?t=251868&highlight=open+office+ascii)

Responses are appreciated.

---

### Post by RequinB4 on 2009-01-21
Right click a pdf file, open with, and choose to open with evince (document viewer).

Also, what is the output of ```
whereis soffice
```

---

### Post by LindaLou on 2009-01-21
Right click and open with document viewer works fine.  Double clicking any pdf file gives me the ASCII Filters Option window.  

Right clicking and selecting Open with Oo Word/Spreadsheet/Document viewer" does work.  

I am still unable to open any documents from the "download" request within Gmail emails.  Any downloads from MS that I "save" will not open from a right click and selecting "Open with Oo Spreadsheet".

Here is the result from terminal you requested:

ndr@ndr:~$ whereis soffice
soffice: /usr/bin/soffice
ndr@ndr:~$

---

### Post by RequinB4 on 2009-01-21
My bad, i  meant go to right click, PREFERENCES, and change what it defaul opens with.

Right click your menu, edit menu, go to your OOo shortcut, right click and edit (or it  might be a button on the side) and paste what the command is.

---

### Post by LindaLou on 2009-01-26
Ok, first I now have Oo available.  Not sure what happened - it was always there, but just wouldn't open (my #4 now solved).  And I any Oo Word or Spreadsheet- old or new - now opens without a glitch - my #2 & 3 now solved.  Documents of any format now can be saved and/or downloaded from any email source or website - my #5 now solved.

The only outstanding issue is the ASCII Filter Options window that pops up each time I want open a PDF file.  I am able to right click on the file and choice "Open with "Document Viewer"".  But I would really like to know why the ASCII window pops up and how to resolve it so that it doesn't pop up when I single or double click a PDF file.

I must apologize here because I don't really understand your instructions.  Would be kind enough to send them again with some more details.

---

### Post by RequinB4 on 2009-01-26
> **LindaLou said:**
> 
The only outstanding issue is the ASCII Filter Options window that pops up each time I want open a PDF file.  I am able to right click on the file and choice "Open with "Document Viewer"".  But I would really like to know why the ASCII window pops up and how to resolve it so that it doesn't pop up when I single or double click a PDF file.

[http://linux.about.com/od/ubuntu_doc/a/ubudg10t10.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg10t10.htm)

---

### Post by LindaLou on 2009-01-26
Ok, I followed the instructions and THANK YOU VERY MUCH!!  Issue solved and I send you large amounts of gratitude! =D>  You have no idea how frustrating this was, especially when I had no idea how this whole "mess" started!!!   :D:KS

---

### Post by randomlyrandom on 2009-02-10
Hi LindaLou,

How is your problem of opening MS office files solved? Can you please explain? What did you do so that when you open word or ppt files without gettnig a ASCII Filter options window and displaying the file properly.

Regards,
-P

---

### Post by LindaLou on 2009-02-10
Hi Pnagral,

Problem was solved and my thanks to RequinB4! Here is the step by step resovle

1.  Right click on the document and choose "Properties"

You will see 5 Tabs - Basic, Emblems, Permission, Open With, Notes, Documents 

2. Click on "Open With"

3. You should see the application (i.e.Document viewer for PDF, Spreadsheet for Calc). Click on the "button" next to the application and click on "close"  That will do it!

4.  If the application is not listed, click on "Add" button at the bottom of the window and choose the application.  

5. Click "Add".  

6. Click on the "button" next to the added application.

7. Click "close"


Here's the link that was provided, gratefully, by RequinB4
RequinB4.

The thread is not marked solved as that option has been disabled, temporarily.

---

### Post by randomlyrandom on 2009-02-10
Thanks.

You mean to say bu doing that your ASCII Filter Options window never appear when you try to open MS office files like .doc, .ppt and .xls files which are stored in your NTFS partition in case if u have dual boot, i.e. WinXP and ubuntu?

I am struggling a lot to open MS office files using Open office. Every time it asks for ASCII filter options and none of the combinations are working for me. They just show junk characters.

Regards,
-P

---

### Post by LindaLou on 2009-02-11
I have MS files (doc, excel, ppt) and since following RequinB4's instructions, which I gave you, all works fine.Give the instructions a try. Then post back.  OK?

---

### Post by byline on 2011-09-18
I'm having the same problem as pnagral, only it's with a couple of old AbiWord documents, both were saved in Rich Text Format. When I try opening them with AbiWord, I can see the original text, but it's imbedded in a bunch of formatting gibberish. If I open them with OpenOffice, I get the ASCII Filter Options box. I click OK, and it opens the document, but with the same formatting mess.

I tried following RequinB4's instructions (going to Properties, going to Open With and then clicking either on AbiWord or OpenOffice, then hitting Close), but neither option changed anything; lines upon lines of formatting code are still there.

---

