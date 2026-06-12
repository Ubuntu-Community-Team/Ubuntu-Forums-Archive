---
title: "Problematic printing of postscripts, on a Brother HL-2040."
date: 2005-10-26
forum: Desktop Environments
---

### Post by Espy on 2005-10-26
So, I'm on an out-of-the-box (when it comes to printing) installation of Breezy, trying to print some notes for class.  They're converted to 6-up postscripts (six logical pages per physical page) from 1-up using 'psnup -r -6 -m5 -b5 -pletter'.  In the Document Viewer application, the document looks like it should, with the logical pages displayed on alternating sides of the physical page.  Likewise, when converted to PDF using ps2pdf.  But after printing the postscript (from the command line or from the Document Viewer), the paper has all the odd-numbered logical pages, and no even-numbered pages.  

What I mean is, a physical page with logical pages displayed like this:

1 2
3 4
5 6

... is printed like this:

1 1
3 3
5 5

:???: 

Now, I have a Brother HL-2040 printer, and the closest driver coming with Ubuntu is labeled for the HL-2060, but other than this problem, it's worked fine before.  I'm thinking that it's a driver issue, which I haven't had time to look into, but I thought I'd throw it out there in case somebody has any genius ideas.  I can print the PDFs okay, but the text quality is crummy.

Thanks for any suggestions!

SP

---

### Post by Stormy Eyes on 2005-10-26
I have one of these printers, but I've never tried doing what you're trying to do.

---

### Post by Espy on 2005-10-26
Have you printed any postscript files that worked OK?

I should have titled this "Problematic printing of postscripts, Breezy Badger, Brother HL-2040".  That would have been awesome.  Damn.

SP

---

