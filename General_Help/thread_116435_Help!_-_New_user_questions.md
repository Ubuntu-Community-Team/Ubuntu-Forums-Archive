---
title: "Help! - New user questions"
date: 2006-01-12
forum: General Help
---

### Post by MJSOnline on 2006-01-12
Hi all.  I have a few questions, I hope you can answer them or point me in the right direction.

What file system do I format my hard drive for it just to store data, mp3, doc etc?  I want to format it in ext3, but there is more options to choose from such as /boot, etc.  What do they all mean?

II am also looking a packjage tghat works like dvd decrypter.  Is there an alterative in Linux?

How do I setup  network printer in Ubuntu?  I have set my HP LaserJet 3320N MFD using Unix in the System > Admin > Printers, but it spools it very slowly. It took over 5mins to print 1 sheet of text.

I am also looking for a package that I can use that lets me print images/text to a printable CD/DVD using my Epson R300 printer.  Any ideas?

How do I "backup" the updates, that Ubuntu downloads for updating my system, to disc/CD?

Is there a list of Terminal commands and what they all do / look like?

I may have more questions to follow, sorry.  I hope you all can help.  Many thanks in advance.
Matthew

---

### Post by TheForumTroll on 2006-01-12
[QUOTE=MJSOnline]
Is there a list of Terminal commands and what they all do / look like?
[/QUOTE]
The list wouldn't fit in the forum ;)

---

### Post by Sepht on 2006-01-12
[QUOTE=MJSOnline]
What file system do I format my hard drive for it just to store data, mp3, doc etc?  I want to format it in ext3, but there is more options to choose from such as /boot, etc.  What do they all mean?

II am also looking a packjage tghat works like dvd decrypter.  Is there an alterative in Linux?

How do I setup  network printer in Ubuntu?  I have set my HP LaserJet 3320N MFD using Unix in the System > Admin > Printers, but it spools it very slowly. It took over 5mins to print 1 sheet of text.

I am also looking for a package that I can use that lets me print images/text to a printable CD/DVD using my Epson R300 printer.  Any ideas?

How do I "backup" the updates, that Ubuntu downloads for updating my system, to disc/CD?

Is there a list of Terminal commands and what they all do / look like?

I may have more questions to follow, sorry.  I hope you all can help.  Many thanks in advance.
Matthew[/QUOTE]
Ext3 is probably the best filesystem for you, it has the best history of protecting files from whiping away magically. just leave the whole partition in ext3. (/boot is loaded during boot and is where the kernel is kept, so some people do something expiremental for their main partition but keep their kernel on something a bit safer)

Yes there is, but I can't tell you what it's called :-D

look in /var/cache/apt/ , it has all the packages you've downloaded. and there are very few "terminal commands" what you want is ls, rm, cd, etc. all of those are actually their own little applications. look for some linux new user guides.

---

### Post by Zimmer on 2006-01-12
[QUOTE=TheForumTroll]The list wouldn't fit in the forum ;)[/QUOTE]
For some basic info on Terminal commands, have a look here
[http://tille.xalasys.com/training/tldp/ch02s02.html](http://tille.xalasys.com/training/tldp/ch02s02.html)

regards

---

### Post by MJSOnline on 2006-01-13
Hi again.  Thanks for the help with the above.

I am also looking a packages that works like DVD Decrypter & DVDSrink. Is there an alterative in Linux?

Can I install my Epson Print CD into Ubuntu using wine?  How do I go about this?

Thanks again.
Matthew

---

### Post by cotcot on 2006-01-13
You could give "dvdrip" a try. It is in the breezy repositories.

---

