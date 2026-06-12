---
title: "Thunderbird logs?"
date: 2006-07-05
forum: Desktop Environments
---

### Post by ceargle on 2006-07-05
Just wondering if Thunderbird logs mail server connections, or more specifically POP3 connections.  I am having problems with mail retrieval timing out at certain times during the day, and want a log to show my apartment's IT guy.  

I've also tried to find POP3 connection logs, independent of Thunderbird, but couldn't find anything.  If anyone could point me in the right direction it would be greatly appreciated.

---

### Post by Centaurette on 2008-06-16
I know this is a few years late, but I have an answer that would help someone searching for this same thing.
On my laptop, this is where I find the log files:
My Computer> C:> Documents & Settings> *identity (the one you are currently using)*> Application Data> Thunderbird> Profiles> *.default (* being a generated alphanumeric combo)> extensions>.  At this point, if you have more than one folder here, look in each of them and look for a folder called "logfiles" (minus the ").
You might have a lot of them...these can also take up a LOT of memory. :mad:  I couldn't figure out why I only had 137Mb left on my harddrive and after much searching around, I found this folder.  In two week's time, Thunderbird had saved 514 logs and it took up 1.99Gb.  I haven't found out how to stop the logging as I don't need it, but that's another thread.  So, if you are having trouble or if you suddenly lose disk space after installing Thunderbird, clean out your logfiles folder.
Hope this helps anyone who comes across these issues.

---

