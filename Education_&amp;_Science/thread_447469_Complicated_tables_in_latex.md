---
title: "Complicated tables in latex"
date: 2007-05-18
forum: Education &amp; Science
---

### Post by aquavitae on 2007-05-18
Hi
I'm writing a specialised accountancy program whcih generates long latex tables as its output, and I want a running total at the bottom of each page.  The problem is this: In order to know what the total is, I need to add up the numbers on the page, but I don't know where the page break is until latex comiles it, by which stage its too late.

Does anyone have any suggestions about how I can get a running total at the bottom of the page, or even whether latex is the right way to do this.

---

### Post by girishv on 2007-05-18
Hi,

you can use longtable and introduce manual breaks where ever you want to.

Girish

---

### Post by engla on 2007-05-18
Latex is not easy to use as a spreadsheet. Perhaps you can do it, but it is not easy.

For latex, you should calculate the totals yourself or in the previous application.

---

### Post by xadder on 2007-05-18
I also think this sounds hard and error-prone to do in LaTeX alone. 

I would write a script (e.g. in perl or python or your favourite programming language), to make one table at a time and print out to a file with LaTeX formatting. Perhaps to a set of files which can be 'includ'ed within your laTeX document. This would be much easier to write and check.

---

### Post by aquavitae on 2007-05-18
The trouble is I have no idea where to put manual breaks.  I can calculate the total in my app easily enough, but I don't know how to get it into the longtable.  I've tried a few things but it seems the basic problem is how to have different text in the \endfoot on each page.  It the moment I'm almost tempted to do the table from scratch using boxes!

---

### Post by Steveire on 2007-05-18
Can you complie it to a dvi or ps file and then add a row for the total on each page with a simple script?

Not sure if those files are easily edited, but look into it.

---

### Post by xadder on 2007-05-18
Do you need to use longtable?  Why not use a new table on each page. I think you can fix Table numbering in other ways if you want that, and you could then hard-code the number of lines in the table on each page.

---

### Post by aquavitae on 2007-05-19
I don't really need to use longtables at all, and I'm not numbering the tables (as there's only one) so that's not an issue either.  I've been looking at using separate tables on each page, but unfortunately the rows are not all the same height - there is a description column which contains a lot of wordwrapped text.  I could do it if I could work out where latex will put the page break then do it manually, but I don't know how to do that.  I've tried experimenting with boxes but haven't got anywhere so far.  Any hints?

---

### Post by ddemerre on 2008-12-16
Well,... maybe this answer is too late, or maybe not... 
What I was thinking,
If you would add a column to each row, containing the total up to the previous line,   You should somehow be able to extract that value (in \latex itself), once the end of the page is reached..., and for non end-of-page rows, That column should/could be made invisible ?
Probably would require writing your own tabular for this purpose...

Any ideas ?

---

