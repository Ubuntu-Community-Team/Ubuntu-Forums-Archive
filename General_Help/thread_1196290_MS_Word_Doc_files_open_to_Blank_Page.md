---
title: "MS Word Doc files open to Blank Page"
date: 2009-06-24
forum: General Help
---

### Post by sandman3838 on 2009-06-24
Here is a strange one!
This all has to do with how opening DOC and XLT files act with both Office and MS Office 2007.

OpenOffice is fine for opening either file type DOC or XLT, no matter how I open any file!

ISSUE - Now with Ms Office 2007:

1. WORKS - If I open Word first, select FILE - OPEN and then the file, the DOC file opens. No problems!

2. FAILS  - If I right click on a *.DOC file and select “Open With Microsoft Word 2007” It FAILS! All I get is a MS WORD and a blank white page.  As if I had opened a NEW document.  There is no text that was saved before.

Now with Excel and *.XLT file I don’t have this issue. These files open just as with Open Office. No problems no matter how you open the files.

I have come across others who have had this issue but there has been no really definite fix or work around.

Suggestions anyone?

---

### Post by sedawk on 2009-06-24
Test 1:
 What happens if you do a double-click on the file. Does it 
 open with Word and work or fail?

Test 2:
 Create a new but empty myempty.doc file.
 Then open it using the context menu (which as you said will
 always open a blank document).
 Enter some words into the blank document and press "save"
 (not "Save As"). Any error or message?
 Now if you open the file with the context menu is it empty again
 or okay? If it is empty again - are the words there if you open
 it the "normal" way?
 
Test 3:
 Create a new empty myempty2.doc file.
 Open it using the context menu (blank file anyway ...) and
 say "Save As". Anything funny about the default location
 offered for "Save As"?. Does saving in that "default" directory work?

(There seems to be something wrong with the action behind
 "open with word" in the context menu or opening a file that
 way involves some temporary directories that are messed up, e.g.
 no write permission or whatever. Try Microsoft's Knowledge Base
 or a Service Pack for Office or ...)

---

### Post by sandman3838 on 2009-06-24
Test 1:
What happens if you do a double-click on the file. Does it
open with Word and work or fail?

PASS - With File Properties at Open with OOfice Word as default, Doc file Opens right up.

FAIL - With File Properties at Open with MS Ofice Word as default, Doc file Opens to a blank page.

(I just wanted to see if there would be a difference between the two)


Test 2:
DONE - Create a new but empty myempty.doc file.

DONE - Then open it using the context menu (which as you said will
always open a blank document).

ISSUE - Enter some words into the blank document and press "save"
(not "Save As"). Any error or message?

PROBLEM - "SAVE" OPENS UP TO "SAVE AS" STILL I SELECTED "myempty.doc" AND I TOLD IT TO REPLACE THE FILE.

ISSUE - Now if you open the file with the context menu is it empty again
or okay? If it is empty again - are the words there if you open
it the "normal" way?

PROBLEM - EITHER FROM CLICKING ON THE FILE OR FROM THE CONTEXT MENU myempty.doc IS A BLANK WHITE PAGE.

Using MS Word Only and as the Default program for DOC files:

Test 3:
Create a new empty myempty2.doc file.
Open it using the context menu (blank file anyway ...) and
say "Save As". Anything funny about the default location
offered for "Save As"?. Does saving in that "default" directory work?

AGAIN - SAME ISSUE 

Note in case it may have been a location or permissions issue I repeated this to another file right to my desktop.  The only way I could see the text was to open the file with OOpenoffice Writer.

This is a strange one? 
Thanks for your help.  Any more ideas?

---

### Post by cbanakis on 2011-05-01
I am having the same issue.

No big deal since I can still open word files.

But if anyone has a solution, that would be super

---

### Post by cbanakis on 2011-05-02
I figured it out.

You need to tell the file to open with wine.  (Not With MS Word Directly)

That was easy enough.

---

