---
title: "how to run acrobat professional ??"
date: 2006-10-29
forum: Desktop Environments
---

### Post by kakyoism on 2006-10-29
I know we got acrobat reader already, but I'd like to mark my PDF's when I read. I tried to wine my windows' acrobat with:

wine "'/media/sda5/Adobe/Acrobat\ 7.0/Acrobat.exe'"

but i got errors:

wine: cannot find '/media/sda5/Adobe/Acrobat\ 7.0/Acrobat.exe'

the path is right
any ideas?

Thank you.

---

### Post by taurus on 2006-10-29
If you use " ", then remove the \ in your path!!!

---

### Post by kakyoism on 2006-10-29
sorry, even if I've done that,
I got the same error message...:(

---

### Post by taurus on 2006-10-29
```
sudo wine "/media/sda5/Adobe/Acrobat 7.0/Acrobat.exe"
```
Better check to make sure you have the capital letters in the right place!!!

---

### Post by kakyoism on 2006-10-29
you are right, now I found the right place but here comes the real problem...

err:module:import_dll Library MSVCP71.dll (which is needed by L"Z:\\media\\sda5\\Adobe\\Acrobat 7.0\\Acrobat\\Acrobat.exe") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"Z:\\media\\sda5\\Adobe\\Acrobat 7.0\\Acrobat\\Acrobat.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\sda5\\Adobe\\Acrobat 7.0\\Acrobat\\Acrobat.exe" failed, status c0000135

---

### Post by taurus on 2006-10-29
I suppose you already configured wine with winecfg!!!

---

### Post by kakyoism on 2006-10-29
Yes, I configured with steps:

1.add application Acrobat.exe according to the path
2.select the added application and go to the tab Libraries
3.added a dll "MSVCP71.dll", then edit it to be native(windows)
later I tried edit it to become Builtin (wine)

It gave me the same error
err:module:import_dll Library MSVCP71.dll (which is needed by L"Z:\\media\\sda5\\Adobe\\Acrobat 7.0\\Acrobat\\Acrobat.exe") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"Z:\\media\\sda5\\Adobe\\Acrobat 7.0\\Acrobat\\Acrobat.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\sda5\\Adobe\\Acrobat 7.0\\Acrobat\\Acrobat.exe" failed, status c0000135

Help please!!

---

### Post by kakyoism on 2006-10-29
help.....

(a man is dying)

---

### Post by kakyoism on 2006-10-30
up, 
i'll wait till someone comes!

---

### Post by kakyoism on 2006-10-30
help!

---

### Post by meng on 2006-10-30
According to the winehq Application Database, Acrobat doesn't work very well in wine anyway, and many people seem to have trouble installing. If you really need Acrobat Pro, perhaps you should look into Crossover Office instead.

---

### Post by kakyoism on 2006-10-30
help.....

---

### Post by meng on 2006-10-30
Ah I see, obviously I was wasting my time and yours by searching for more information on the topic. Goodbye.

---

### Post by kakyoism on 2006-10-30
sorry, didn't realize there was another page...
thank you very much !

(signature very funny~)

---

### Post by meng on 2006-10-30
Pardon me, I was overreacting to being ignored. There are some documented experiences of wine and Acrobat here:
[http://appdb.winehq.org/appview.php?iVersionId=4922](http://appdb.winehq.org/appview.php?iVersionId=4922)

---

### Post by the79bomb on 2007-03-05
What you do is copy the 2 dll files from windows/system32 into the same folder as acrobat.exe  this will allow acrobat to start.  

However on my system It crashes after a few seconds and gives a long error message.  I would be very anxious to get some help with that.  I have attached the error message in case anyone is capable of understanding it.   Says something about invalid window height/width and a load of other stuff.   Any help would be MUCH appreciated.
Thanks, Tim

---

### Post by jetpeach on 2007-03-06
i am the "maintainer" of the acrobat page on WineHQ and have been wanting Acrobat Full on Linux for over a year now.  I have tried various tricks, a little with shuffling windows libraries into wine, but as of yet I have not had success.  Some people on the wine page have apparently gotten it working.  I can install it and it even runs and seems to be working fine, but then withint about 5 seconds it kills itself - it seems it does because of license issues.  Wine does not have the license checking capabilities Acrobat needs so either Wine (or Acrobat when license checking fails) terminate the app.

If you have any luck, please post on the WineHQ page and let the rest of us know. I guess there is not that much demand for Acrobat full (people are always like, "just use reader" or "pdfs aren't meant to be edited" and they simply don't understand. i obsolutely require highlighting and note taking in PDFs for my work.)

so alas i duel boot windoz still...

---

### Post by the79bomb on 2007-03-25
I receive scanned documents in PDF format and I have to type them in for work.  Acrobat's OCR feature is awesome for this. Saves hours of typing.  If anyone knows of a similar program that will OCR PDF's I would be very interested.  Until then, Dual boot unfortunately.

---

### Post by jetpeach on 2007-07-22
just to let people know, there have been continued improvements to wine and somebody says it's working for them.  i was excited and tested, but although the install seemed to work fine, it still quits about 10 seconds after loading. i can even load PDFs and see them and everything, but then it quits.

i may try to figure out why, and for some it might work, so if you want to test give it a try - i didn't set up any native DLLs so that may be necessary and why it doesn't work for me still, but it now feels VERY close... the install went really smoothly at least.

the wineHQ app page:
[http://appdb.winehq.org/appview.php?iVersionId=4922&iTestingId=13121](http://appdb.winehq.org/appview.php?iVersionId=4922&iTestingId=13121)

also, i saw this page describing how to get photoshop working and somebody commented if it might work on acrobat as well. with some testing, it might work (i'd like to try at some point in the future and will update if i do).
[http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps](http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps)

---

### Post by Loanarn on 2008-04-11
> **jetpeach said:**
> just to let people know, there have been continued improvements to wine and somebody says it's working for them.  i was excited and tested, but although the install seemed to work fine, it still quits about 10 seconds after loading. i can even load PDFs and see them and everything, but then it quits.

i may try to figure out why, and for some it might work, so if you want to test give it a try - i didn't set up any native DLLs so that may be necessary and why it doesn't work for me still, but it now feels VERY close... the install went really smoothly at least.

the wineHQ app page:
[http://appdb.winehq.org/appview.php?iVersionId=4922&iTestingId=13121](http://appdb.winehq.org/appview.php?iVersionId=4922&iTestingId=13121)

also, i saw this page describing how to get photoshop working and somebody commented if it might work on acrobat as well. with some testing, it might work (i'd like to try at some point in the future and will update if i do).
[http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps](http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps)

Just throwing my 2 cents in. I work for adobe tech support and get calls on this issue in acrobat all the time even in regular windows environments. Its true this is a licensing issue. 

Generally speaking the cause is because the user account the customer is running in doesn't have the proper permissions to read or write the activation file. 

A few things we do generally speaking is create new user account off of domains if the are on domains because the domain can strip user rights even if the user is an admin. We also run cacls or icacls respectively on the parent folder of the activation file and all its subfolders. On XP its located in C:\docs and settings\all users\app data\flexnet. The file is called adobe adobe_00080000_tsf.data. In vista it is C:\program data\flexnet. If the file exists we generally move it out of the folder and try relaunching the program to prompt for activation on startup. 

If it cannot properly read or write to that file the program will close without an error after approximately 10 seconds. The last thing i generally try is to make sure that the flexnet licensing services is started and set to automatic. If the service doesn't start there is a good chance you wont be able to activate. Its true that the licensing service touches a few of the dlls although i cant remember which ones off the top of my head. I hope that may give you a bit of inspiration.

---

### Post by lkilcher on 2008-04-18
So, just out of curiousity, is anyone over at Adobe making any effort to make an Adobe Professional/Standard linux version?

And yes I, like jetpeach, have heard all the arguments:
"pdf's aren't meant to be edited"
"just use reader"

And yes, there is the issue of whether or not such an application would sell to a community of users dedicated to open software.  I will say this though, in spite of my strong feelings for open-source software, I WOULD BUY adobe acrobat pro for linux, for the following simple reason:
I need to be able to write notes on, and highlight sections of the journal articles I read.

I prefer to read the articles on my screen (rather than on paper).  I prefer for my notes to be electronic (so I don't loose them if/when I loose the paper copy of the article).  As it is now, I write a separate Article.notes.tex file for each article.  It's frustrating and inefficient to have the notes separated from the document though.

Of course, if Adobe doesn't jump on this, it is possible that someone will develop an open pdf-editor:
pdfedit might be headed in the right direction, but the interface has a LONG way to go... and it also might be too general.  Truly, all I want is to be able to highlight text, and add/edit notes.  Is that too much to ask?  What if pdfedit had two modes:
1) "Simple mode" simple scrolling, reading, note, highlight functionality.
2) "Full mode" tear your pdf to pieces and reassemble it however you like!

Is this being discussed anywhere else?

Thoughts?

If this isn't fixed by the time I get done with Grad School, look for me to be working on it.

Also, FYI: I haven't tried using wine w/ adobe-pro.  I prefer native apps... mostly because wine sounds like a pain, and this is THE ONLY app I haven't found a native replacement for.  If the wine fix gets to a place where it sounds stable, I might give it a try.

---

### Post by jdrodrig on 2008-05-03
Just to keep this thread updated, I thought of sharing that there is another propietary software for linux that can edit PDFs: PDF Studio [http://www.qoppa.com/psindex.html](http://www.qoppa.com/psindex.html)

The main problem I have found with other opensource editing software for PDFs under Linux is that if I open a highlighted pdf back in windows acrobat standard or reader, the highlighted text is not shown. So far, this PDF studio does the trick; the comments and higlighthing appear OK in standard Acrobat.

---

### Post by cuz on 2008-07-23
As another grad student, I'm with lkilcher on the need for this app. I keep trying PDFEdit, but it doesn't quite cut it yet. I suppose I will try the demo version of PDFStudio. And frankly, when I used Windows, Acrobat Pro was one of a small handful of programs that I actually did pay for. If you're trying to be environmentally responsible, there is no other option but to mark documents electronically. I've even graded papers this way.

Two additional thoughts:
1. OpenOffice 3.0 is supposed to come out in the fall with some limited pdf editing capabilities. Perhaps this will be sufficient.
2. Rather than making separate notes files, lkilcher, I use bibliographic software, which provides lots of other advantages as well. (Presently JabRef, but OpenOffice 3.0 may get much stronger bibliographic capabilities as well, and I'll definitely try that out.)

---

