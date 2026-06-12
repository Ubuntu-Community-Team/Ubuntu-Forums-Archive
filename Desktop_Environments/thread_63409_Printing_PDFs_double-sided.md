---
title: "Printing PDFs double-sided"
date: 2005-09-07
forum: Desktop Environments
---

### Post by wastrel on 2005-09-07
I need to print PDFs regularly and would prefer to print them double-sided in 
order to save paper, but I don't currently have an easy way to do this.

I'm using Hoary, and have CUPS.  My printer is anEpson Stylus C86, and I've 
configured CUPS to use the Stylus C82 driver, there being now C86 driver 
currently listed.

I can print fine from xpdf or evince but am unable to print from ggv, which I 
have used in the past to print double-sided.  

So, I'd either like advice on getting printing working from ggv, or on how to
 print double-sided with another PDF viewer.  

ggv has no print configuration options that I can locate but allows you to easily 
select just odd or even pages for printing.  When I try to print from ggv it just sits 
there and does nothing.  I don't get any messages in /var/log/cups/error_log, and 
no print jobs start in the print queue.

In other pdf viewers I am unable to limit print jobs to just odd or even pages, I can 
only select ranges of pages to print. 

Any ideas?

---

### Post by NetDiver on 2005-09-22
I have the same problem.
Why there is in the standard gnome printing dialog not the possibility to choose to print odd and even pages.
At the moment, the two pages on one function is also not working. It is just ignored. I hope its because i'm using  Breezy Development.
Any ideas or workarounds?

---

### Post by chunk on 2006-01-24
Has anybody found a solution to this problem?

---

### Post by wastrel on 2006-02-17
I installed kpdf and am using the kde printing dialog which does allow printing odd or even pages only.

This is the simplest solution I've found.

---

