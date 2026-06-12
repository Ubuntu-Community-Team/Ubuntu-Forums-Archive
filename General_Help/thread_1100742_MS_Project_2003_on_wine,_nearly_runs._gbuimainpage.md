---
title: "MS Project 2003 on wine, nearly runs. gbui://mainpage.htm error."
date: 2009-03-19
forum: General Help
---

### Post by BFG on 2009-03-19
I've installed MS Project 2003 onto 8.10 intrepid using wine 1.0.1.

Office (word + excel) installed fine and work well.  But, the MP Project install complained "Cannot launch wscript.exe" and wouldn't run.  It seems that MS Project requires IE in order to run, but I tried copying wscript.exe across from an XP install and this took me a step forward.  
This resulted in an error:
The command is attempting to use a webpage from the site gbui://mainpage.htm. You have not identified this site as a trusted site in Internet Explorer.

I installed IE fully using IEs 4 Linux:
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

But the error persists.
MS Article: [http://support.microsoft.com/kb/887028](http://support.microsoft.com/kb/887028)

Now the bit where I get stuck.  I'm a wine novice, and the system.reg holds some mystery.  Is there a way to transpose the registry edits advised by MS into wine's registry?

Any hints appreciated. :D


[SIZE="1"]Unfortunately collaboration dictates the use of MS Project, so Planner 0.14.3 (which I have installed) is not a viable alternative.[/SIZE]

---

### Post by CrusaderAD on 2009-03-19
Unfortunately I can't offer much help in regards to this (you probably saw you got a response and got excited for a second, sorry). But in my experience, everything NEARLY runs with Wine. They should call it "Whine".

---

### Post by BFG on 2009-03-20
> **raptormanad said:**
> They should call it "Whine".
:lolflag:


I live in hope ;)

---

### Post by RikoW on 2009-03-20
Hi,

this may not be the answer you are looking for, but I'm running Project 2003 just fine using Codeweavers Crossover Office. Depending on how necessary it is for you, you may be willing to spend those 40 Euro for a lincense (and support the wine project at the some time).

They have a trial version for 30 days, which you can test.

BTW: I don't think, installing IE via IES4LINUX will help you in any case. Your project installation will not know anything about your IE installation, since (most likely) they are in different wine bottles (so to speak on independent windows systems).

Good luck,

              Riko

---

### Post by BFG on 2009-04-09
Thanks Rikow, I'll check it out. :)

---

### Post by BFG on 2009-05-20
Works perfectly!  Thanks again.:KS

---

### Post by mdalacu on 2009-12-17
It working perfectly if you do everything from this article: [HTML]http://support.microsoft.com/kb/887028[/HTML].
Tested with Wine 1.1.34 and MS Proj 2003 sp2. I've also have installed via PlayOnLinux, IE6.

---

### Post by xbartolo on 2012-12-14
In my case what it worked was to install Internet Explorer in the wine installation where MsProject was installed. 
After that it worked fine

Hope it helps!

---

### Post by Toz on 2012-12-14
Thanks for sharing, but this thread is almost 3 years old - a lot has changed since then. Closing.

---

