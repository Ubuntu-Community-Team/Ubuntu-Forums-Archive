---
title: "OpenOffice 2.4.1:Strange  Problem in PDF-Export if a writer-doc contains formulas"
date: 2008-08-06
forum: Desktop Environments
---

### Post by hal10000 on 2008-08-06
Hi,
i hope this is the right place to for my problem, if not, feel free to move it to a correct place.

I have a very strang problem with OpenOffice 2.4.1, which came up in the last two weeks.

When exporting a text document to PDF and the doc contains formula, then the created pdf-doc sometimes shows in the formula-blocks strange characters (I guess they are arabic characters instead of latin)
In the origenal OpenOffice document the formula is displayed correct, only the created pdf-doc shows malformed data.

What's confusing me is that only some of the characters are malformed and others not, this often changes in one formula-block.

What's confusing me more is that if reexport the doc to PDF without making _any_ changes, then the PDF-Document may then show the former malformed parts correct while other parts instead are malformed.

And what's confusing me most is that if i take the original OpenOffice Document and carry it to another computer and then exporting it to PDF then everything is displayed correct in the PDF-Doc.

I googled for this behaviour and also searched some forums, but didn't find anything.

Any help is appreciated very much, because i often need to export Office documents containing formulas for teaching purposes.

The first attachment shows the original OpenOffice Document and the second is the same part of the exported PDF-File.

---

### Post by tchu on 2008-08-30
I have the same problem with a text document with mathematical formulae added using OpenOffice Maths after exporting it as PDF. I have a workaround by using 'Print to PDF' which comes with Ubuntu. Press Ctrl+P in OpenOffice and the document should be "printed" as a PDF file stored in /home/[your own username]/PDF folder.

This should all have been pre-installed and you should not need to do this, but if not here are the instructions:

1. In control centre (type gnome-control-center in terminal), go to 'Personal' section and click on 'Sessions'. Under 'Startup programs', make sure 'Print queue applet' is enabled.

2. Go to 'System' section and click 'Services', make sure 'Printer services (cupsys)' is enabled.

3. Go to 'Hardware section' and click on 'Printing'. See if 'Print to PDF' is under Local Printers. If not, click 'New Printer', select 'Print to PDF file' then 'Forward', select 'Generic' then 'Forward', select 'PDF file generator' then 'Forward', change the names as you wish then 'Apply'.

---

### Post by hal10000 on 2008-08-30
Thanks for the tip. I've already thought about printing to a pdf-printer, but could'nt imagine that it makes a difference.
When i read your posting, i tried it and it works perfectly.

Have a good time.

---

### Post by Koterpillar on 2008-10-20
Same problem, and PDF printer solved it.
Waiting for OOo 3.

---

### Post by clemente on 2009-02-12
Hi all, 

IMHO there is no corresponding bug reported, yet. Can you please report this issue at [https://launchpad.net/ubuntu]("https://launchpad.net/ubuntu") to give those guys a chance to fix it? Even if your postings are somewhat old - this issue seems still to be unfixed. ;-)

I use Ibex (8.10) and cannot confirm - and for that report - the bug. I just know about a Heron (8.04) user with the same problem. 

Thanks a lot, 
Clemente

---

### Post by manoskats on 2009-06-02
Hi all,

I have the same problem when I export to pdf.
when I use the ctrl+p workaround the formulas are exported correctly but now the text comes out corrupted,probably because it is in greek (text in english is unaffected).

Can you help me with this?
Apologies if it is a newbie question.

---

### Post by [Neurotic] on 2009-07-03
For those who may be looking for it, there is a bug report here:
[https://bugs.launchpad.net/openoffice/+bug/281234](https://bugs.launchpad.net/openoffice/+bug/281234)

---

### Post by 4ebees on 2010-01-20
A year and a bit later and this is still good advice :)

Thanks for that. I'd not had problems with Open Office printing to PDF until I installed Karmic 9.10.

This solved the problem as I can now use the 'print to pdf' option within OO.

Again, many thanks.

---

### Post by hal10000 on 2010-01-20
I marked this thread as SOLVED, although it's more a wokaround than a real solution to use a pdf-printer.

---

### Post by simosx on 2010-03-13
> **hal10000 said:**
> I marked this thread as SOLVED, although it's more a wokaround than a real solution to use a pdf-printer.

This is more likely an OOo issue when exporting to PDF.
There have been some improvements in OpenOffice 3.2; give it a try. I expect it should work OK.

---

### Post by Hagar Delest on 2010-03-14
I remember [[Issue] Symbols such as '2' exported as wrong glyphs in PDF]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=12&t=8737").

---

