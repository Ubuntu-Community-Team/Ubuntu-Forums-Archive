---
title: "Firefox printing problems?"
date: 2009-05-07
forum: General Help
---

### Post by stevelt on 2009-05-07
Hi all, 

I have a longstanding issue with printing from Firefox on Ubuntu, and it's driving me mad.  Having searched I don't seem to be able to find any exact matches for the problem so any help much appreciated!

The issue is that when I print one page from firefox, I get one page of A4 (which is correct, the default paper size), then the printer starts spewing out duplicates of "Letter" paper size.

This means I have to either turn the printer off, or force it to print the unwanted duplicates (normally 3 I think) onto the A4 (which is the CUPS default).  This is really annoying!

This issue exists in jaunty, and in at least the last two Ubuntu releases (I have been upgrading for 2+ years)

All other applications print fine to my printers, so I don't think this is a driver or CUPS issue, but rather a Firefox specific one.

Any tips or links to existing bugs/workarounds would be much appreciated!

---

### Post by dandnsmith on 2009-05-07
I'm feeling a little stupid.

Are you saying that you ask to print one page (one copy of it) and get duplicates of that page with the same content as the original, except as Letter rather than A4?

---

### Post by stevelt on 2009-05-07
> **dandnsmith said:**
> I'm feeling a little stupid.

Are you saying that you ask to print one page (one copy of it) and get duplicates of that page with the same content as the original, except as Letter rather than A4?

Yes, thats exactly right.

Here's a worked example :

Right now I'm trying to print a boarding card for my airline flight.  This is 2 A4 sheets.

What happens is the printer prints one A4 sheet (page 1), then repeatedly requests "letter" paper.  If I press "OK" on the printer to override and force A4, then I get numerous duplicates of "page 1", but not any "page2".

This basically means anything printed from firefox has to be cut/pasted into another application before it can be printed.

---

### Post by dandnsmith on 2009-05-08
That's really weird - I could see some logic if the 2nd sheet was printed with the second sheet content (if you see what I mean), but this looks almost as if you're getting an error at the end of each page signalled back, which gets a page reprint request generated (and this continues until forcibly halted).

My prime suspect would be the way the print queue has been set up - in particular that bit which deals with printing from web pages. I did do some analysis when I was getting problems with formatting Man pages for printing in the days of RedHat 7, but haven't looked at it since, as later versions corrected the problem (which was connected with the sizing of A4, which had the parameters wrongly set).

First thing is to assume that there is a problem, delete all the printer queuing and processing stuff and re-install it, looking hard at any parameter setting you have to do on the way. Do test prints for every type it gives an option for.

Another thing to try is a different browser - you might be able to bypass the problem that way.

---

