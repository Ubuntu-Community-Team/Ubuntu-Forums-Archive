---
title: "Wine problem in Maverick"
date: 2010-06-25
forum: Desktop Environments
---

### Post by corradoventu on 2010-06-25
Clickimg CARDFILE.EXE (an old windows 3.1 program) from the WINDOWS partition with WINE in MAVERICK I have the following message. The same works using WINE in LUCID.

Archive:  /media/EAA43BAFA43B7D5F/SCHEDE/CARDFILE.EXE
[/media/EAA43BAFA43B7D5F/SCHEDE/CARDFILE.EXE]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/EAA43BAFA43B7D5F/SCHEDE/CARDFILE.EXE or
          /media/EAA43BAFA43B7D5F/SCHEDE/CARDFILE.EXE.zip, and cannot find /media/EAA43BAFA43B7D5F/SCHEDE/CARDFILE.EXE.ZIP, period.

---

### Post by 3Miro on 2010-06-25
Are you sure you are opening this with wine and not zip. If it is an application, then you need to right-click on it and select "Open With -> Wine". File associations are sometimes messed up for wine, the zip archiver is sometimes wrongfully set up to be the default program for .exe files.

---

### Post by corradoventu on 2010-06-25
yes i'm using'open with wine'. in Lucid it workx with 'open with wine' AND with double-click. in both environments wine is 1.1.42.
bye

---

### Post by corradoventu on 2010-06-25
sorry, i don't noted the difference; opering with wine the message is: 
The file '/media/EAA43BAFA43B7D5F/SCHEDE/CARDFILE.EXE' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.  

from CARDFILE.EXEC properties i see: DOS/Windows executable (application/x-ms-dos-executable)
permissions: read and write, owner: corrado (i'm corrado) but i'm unable to check 'allow executing file as program' if i check the box the check mark appears for a moment and then disappears.

---

### Post by corradoventu on 2010-06-25
in lucid, from CARDFILE.EXE properties permissions the box 'allow executing ..' is checked an i can't UNCHECK ...

---

