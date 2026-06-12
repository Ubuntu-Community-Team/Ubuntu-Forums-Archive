---
title: "MS Word won't open files with spaces in their name"
date: 2009-08-06
forum: Desktop Environments
---

### Post by roystreet on 2009-08-06
Hello, I don't know if anyone has experienced this problem...I have successfully installed & have been using MS Word 2007.  I have just found problem that really stands out.  If I'm looking through some location (Say in my home directory) and I see a word file & I decide I would like to open it.  I click on it...It loads words...Then It breaks apart the name as separate files.  For example: **johnny goes to the store.doc ** Word will say **johnny.doc** *could not be found*, **goes.doc** *could not be found*, **to.doc** *could not be found*, etc.

If I open word & select open, then navigate to that document it then opens the file just fine with no issue.  So through word I can ope it, but no other way.  I have tested it with names that do not have spaces & it worked just fine, so it (at least) has something to do with spaces.

Any thoughts on how to remedy this?  Has anyone else experienced this?

Thanks,
~roystreet

---

### Post by rednano12 on 2009-08-06
The obvious thing to do would be to rename your documents so they don't have spaces. 

Then, I would suggest moving this to a different location, such as Wine.

---

### Post by roystreet on 2009-08-06
Thanks for your thoughts.  I don't know why moving it to wine will help?  Are you talking about moving it to the wine directory?  I haven't fully decided that I will remove spaces out of the names of all my files.  Nor will I place underscores or hyphens there either.  I will just open it with word instead of the other way, I can live with that.

I just didn't know if there was any type of remedy instead of renaming.  

Thanks!

---

### Post by Hobgoblin on 2009-08-06
I think rednano12 means move your thread on the forum to the wine section.

---

### Post by roystreet on 2009-08-06
Thanks for the clarification...

How do I move the thread over - I've never done that before - or do I create a new thread there.

~roystreet

---

### Post by Gogolization on 2009-09-14
I have the same problem with Word documents (oddly enough PowerPoint slides or Excel documents don't have this problem), and find it incredibly annoying since so many Word documents do include spaces. Is there any solution for this?

---

### Post by snakeman21 on 2009-09-14
Why not just use openoffice?  Completely compatible, easy to use, more stable, more versatile... what more could you want?  My wife goes to an "all microsoft" college, but she uses Ubuntu and writes her papers in OpenOffice.  She saves them as Word documents and emails them, and her professors open them with MS Word.  Perfectly compatible.  

Forgive me if I seem like a jerk, but it seems to me that using Microsoft Office on Ubuntu is creating an unnecessary hassle for you.

---

### Post by AlphaLexman on 2009-09-14
I know the original post is quite old, but I seem to remember MS Win ME running MS Word had the same problem.  Back then MS was just adjusting to long filenames compared to the eight.3 format.  If the file has been renamed and the shortfilename didn't make the link/connection it would think each space was a different file.

I know this isn't a solution, but someplace to look into.

---

### Post by roystreet on 2009-11-19
> **snakeman21 said:**
> Why not just use openoffice?  Completely compatible, easy to use, more stable, more versatile... what more could you want?  My wife goes to an "all microsoft" college, but she uses Ubuntu and writes her papers in OpenOffice.  She saves them as Word documents and emails them, and her professors open them with MS Word.  Perfectly compatible.  

Forgive me if I seem like a jerk, but it seems to me that using Microsoft Office on Ubuntu is creating an unnecessary hassle for you.

Hi snakeman21:
...I currently prefer office 2007 over OpenOffice.  I appreciate OO & am willing to consider future builds of it.  I have tried to fully migrate over to it *(More than once)*.  I don't find it as user friendly. Yes, I do like the ribbon :D much better than the old toolbar.  Of course that is just one feature I like better.  Even it's ability to use VBA is wonderful.
...Also, if I make docs in word & then open them in OO I often find formatting has changed.  It doesn't cleanly open all of my word documents.  Also, OO currently doesn't have a database that is nearly as powerful as access.
.
...I honestly believe OO will get there one day.  I can envision myself using it as my default office application one day, but today isn't the day.

Thanks,
   ~roystreet

---

### Post by snakeman21 on 2009-11-19
Eh, to each their own.  It's all about what you're comfortable with!

---

### Post by erikacoustik on 2009-11-26
....bump?

i have the exact same problem as roystreet

---

### Post by roystreet on 2009-12-01
Hi,
...I'm guessing there is no solution to this?  I'm not incredibly smart in this area, but it seems there would be some type of fix?  I'll do some more research - If anyone has some suggestions that would be great!
.
Thanks,
...roystreet

---

### Post by m-a-r-k-y on 2010-01-30
Bump. I am having the same problem as roystreet too.

---

### Post by Mazin on 2010-01-30
Hi all,

I can try to take a stab at this problem.  Does this spaces problem happen when you are opening a file from inside Nautilus (the default Ubuntu file manager) AND when you use Word's built-in file browser (File->Open)?

---

### Post by m-a-r-k-y on 2010-02-02
> **Mazin said:**
> Hi all,

I can try to take a stab at this problem.  Does this spaces problem happen when you are opening a file from inside Nautilus (the default Ubuntu file manager) AND when you use Word's built-in file browser (File->Open)?

Hi Mazin. The spaces problem happens with right click, and "open with >" Microsoft Office Word. I am running Kubuntu 9.10, and the problem happens with all file managers I have tried (Nautilus and Dolphin and Konqueror). When I use Word's built-in file browser there is no problem, and I can open a file with spaces or without.

---

### Post by Mazin on 2010-02-02
The problem is that whatever is launching Word isn't properly wrapping the file name in quotes, so "My Document.docx" is treated as "My" "Document.docx", but working around the problem isn't too hard.

Try these instructions that were suggested on Wine's AppDB and reproduced below. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12811](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12811)

1.  Make a script with the following text
```
#!/bin/bash 
wine "C:\Program Files\Microsoft Office\Office12\winword.exe" "`winepath -w "$@"`" 
```
and save it as "word_launch.sh".  Put it somewhere safe, like your home directory.
2.  Make the script executable (right-click on the script, Properties, Permissions).
3.  Right-click on a Word document, choose Open With and choose Other Application...
4.  Hit the browse button and find the script you just made:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=145788&stc=1&d=1265165415[/IMG]

You will have to make a new script for each different program (Word, Excel, etc.) and repeat steps 3 and 4 for each different file type (.doc, .docx).

In the future, WineHQ's AppDB is always a helpful source of tips and fixes for running Windows programs.

---

### Post by m-a-r-k-y on 2010-02-03
Thank-you Mazin for your help. This solution works well. I no longer have problems opening files with spaces in their names :)

---

### Post by teo_rossi on 2010-04-03
I receive a wine error: the file .../winword.exe does not exist

---

