---
title: "Openoffice.org writer documents get set to (false) read-only"
date: 2010-08-04
forum: Desktop Environments
---

### Post by HandeH on 2010-08-04
Using OpenOffice.org 3.2.0 (with Lucid Lynx). There is a long lasting (already in Jaunty, at least) bug: you cannot edit some .odt documents originally made as .doc. Mine example is a fill-in form made with tables, has a header, is one page long, has a Drawing Object and a Graphics/Picture/bit-map image. 

Sometimes you can fill it in partially, sometimes not at all. When trying to write to a cell of a table, a pop-up announcement comes: 
> Readonly content cannot be changed. 
No modifications will be accepted.

None of the tips I have seen has helped (eg. Format>Sections...>Write Protection). An old thread (in AMD 64 bit section) FYI: [http://ubuntuforums.org/showthread.php?t=839383](http://ubuntuforums.org/showthread.php?t=839383)

How to report this bug?

---

### Post by ytsurk on 2010-08-04
did you hit the read-only button next to the save buttons in the menubar ?!

---

### Post by HandeH on 2010-08-07
;), it's a bug. That button does not change it.

---

### Post by Hagar Delest on 2010-08-07
Can you upload the file somewhere so that we try?

---

### Post by HandeH on 2010-08-09
This one: 
[http://www.kissaliitto.fi/lomakkeet/srk_ilmo.doc](http://www.kissaliitto.fi/lomakkeet/srk_ilmo.doc)
Compare to this RTF, where the header part seems to be broken: 
[http://www.kissaliitto.fi/lomakkeet/srk_ilmo.rtf](http://www.kissaliitto.fi/lomakkeet/srk_ilmo.rtf)

---

### Post by Hagar Delest on 2010-08-09
I don't see the problem. I've saved in .odt and I can fill in the whole form. Activate the fields shadings (Ctrl+F8 or View menu) and then double-click the gray areas to type the text. Of course, if I try to write something outside those areas, I get the read-only message. But unprotecting the section fixes that.

---

### Post by HandeH on 2010-08-09
Please, keep on trying! 

Sometimes you are able to fill in one letter, sometimes half of the form and sometimes you could fill in the hole form. Sometimes you cannot delete contents (typing errors). In these cases you get that erroneous message about write-protection.

---

### Post by mwildam on 2010-08-10
I can reproduce your problem and this occurs when you put the cursor at the end of the input field. Then you can enter exactly one character and after that it shows the error.

It is not the complete document that is read only it is only the field that does not accept any more input. If you position the cursor at the beginning or in the middle then no problem.

Look at the video: [http://www.sendspace.com/file/upgih9](http://www.sendspace.com/file/upgih9)

---

### Post by Hagar Delest on 2010-08-10
Weird, I can't see how you can put the cursor directly in the field. For such input fields, OOo pops up a dialog asking for the data to be entered. I can't type in the middle of the fields (even if it has been already filled in).

---

### Post by HandeH on 2010-08-12
> **mwildam said:**
> If you position the cursor at the beginning ... then no problem.


In this case the problem is that you are not able to delete or add anything to the particular field. 

If you navigate by tab key, you are able to insert two letters or numbers at the time. :rolleyes: and things like that.

---

### Post by mbck on 2010-12-06
I confirm with OOo 3.2.0 on Ubuntu (1:3.2.0-7ubuntu4.1)
(a) If attempting to enter data at the end of a form field entry is not allowed
(b) However, entry of 1 or 2 characters is possible in some cases
(c) Tabbing between fields gets you to a position in fields where the problem does happen,
(d) Such entries cannot be undone (Edit->Undo or Ctrl-Z won't work) or otherwise erased.
Because of (d) it is necessary to close without saving, restore last saved copy and resume data entry from last saved point.

This is a major annoyance.  If the "abnormal entry" could be undone, the issue would be minor.

---

### Post by falsifian on 2012-02-21
I'm on Debian not Ubuntu (Openoffice 3.2.1) but in case it helps anyone, I had to do one thing in addition to mbck's advice to use the tab key: after tabbing to a text field, I have to enter the last character first, and then press the back arrow and type the rest.  If I just tab and start typing, it stops me after two characters.

---

### Post by HandeH on 2012-02-23
On Lucid Lynx with OO.o 3.2.0 the problem still exists and the tabbing does not help. So, here is a work-around, which might feel a bit complicated at first, but it just works. 
[LIST]
[*]Install [Inkscape]("http://packages.ubuntu.com/lucid/inkscape") and [pdfshuffler]("http://packages.ubuntu.com/lucid/pdfshuffler")
[*]Export the problematic document (with tables) as PDF.
[*]Open the PDF with Inkscape and do your editing there one page at a time. Save the completed sheets as PDFs (use Save as...).
[*]If you have a multi-paged document, you have to open, edit and save pages separately in Inkscape. Fortunately, you can very easily merge the single paged pdf files into one individual pdf file with pdfshuffler (drag from Nautilus and drop into pdfshuffler's window).
[*]That's it!
[/LIST]

Inkscape tips: while editing the sheets consider using fullscreen mode by pressing F11. When saving remember to use **Save as** and proper naming for the individual pages, eg. from Document.pdf save as separate pages like Document-page1.pdf, Document-page2.pdf, Document-page3.pdf, and in the end merge with pdfshuffler as Document-ready.pdf.

---

