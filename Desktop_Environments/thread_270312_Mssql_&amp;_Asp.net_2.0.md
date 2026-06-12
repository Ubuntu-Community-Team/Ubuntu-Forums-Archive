---
title: "Mssql &amp; Asp.net 2.0"
date: 2006-10-03
forum: Desktop Environments
---

### Post by jheath on 2006-10-03
Hi there,

I am new to Ubuntu and have recently made the request for some Dapper Drake CD's to be sent my way. My reason for moving to Ubuntu? I didn't like the way Vista was looking and quickly decided to take up an open source OS instead. Besides, this community is huge. ;) 

Anyways' my question is concerning a couple of desktop apps I use or perhaps some alternatives you ubuntu peoples might be able to recommend to me? I am a web developer and as such, I develop in ASP.NET not PHP. And I need to manage a number of MSSQL databases. There is the official Microsoft SQL Server Management Suite however unfortunatley they don't release tasty versions for linux. :-| 

Does anyone here know, how I might be able to enjoy the desktop environment Ubuntu offers and at the same time manage and work on my MSSQL databases and code in a ASP.NET 2.0 and C# environment? Is anyone doing it at the moment?

Thanks for the support! :D

---

### Post by caffine_fizz on 2006-10-28
you can configure asp 2.0 .NET to work with apache through a module called mod_mono; i'm doing somthing similar to you at the moment.
I'm not having much luck with the configuration (2 days so far) and you should also know that 2.0 is not compleatly supported yet.
 On the data base side, i'm a novice to asp 2.0 .NET but i'd be really suprised if you couldn't connect directly to a linux based sql by making manual alterations to you web.config file when you shift it out of windows?
Again should be hitting that soon let you know if i find anything out!

on mod_mono check out these links:
[https://help.ubuntu.com/community/ModMono]("https://help.ubuntu.com/community/ModMono")
&
[http://thoth.robrohan.com/client/index.cfm/2006/10/11/C-Web-Development-On-Ubuntu-Part-]("http://thoth.robrohan.com/client/index.cfm/2006/10/11/C-Web-Development-On-Ubuntu-Part-")

---

### Post by Onomatopoetikon on 2006-10-28
Heyas

mod_mono and Apache can get you a ways with ASP.NET, but 2.0 is not completely supported. Neither is there a way to manage MSSQL databases from Linux, I figure you mean by the way of Query Analyzer and the like. You *could* try to make it all work with Wine, I couldn't. Whereas you can develop for MySql or other db's, the typical ASP.NET setup is for MSSQL or even Access, unless you do your own hosting, off course, then you can choose freely.

I did get mod_mono to work, but then I found myself lacking a decent editor for my ASP.NET pages. I'm personally strictly old school when it comes to programming tools, I use TextPad for Windows whenever I can, but professionally you just can't get around VS.NET or the Express IDE at least. Those programs are not running on Linux, and from what I know nothing comparable exists for ASP.NET. Support is shabby at best for plain editors too.

At the end of the day, I grabbed VMWare Player and put a WinXP machine on it. Works like a charm. I'd advice you to do the same thing. ASP.NET on Linux is still very much in the stone age compared to on Windows, and you know it; all the other kiddies use VS.NET and churn out code by the speed of a 1000 wizards and other hand-holding gadgets. Time is money in programming, if you're just a hobbyist you can ignore it and do it the way you like, but your customers will want to know why your competitors can ship projects in half the time you can.

Someday we might see comparable ASP.NET tools for Linux, it's a strong platform with lots of hype and a million developers going that direction allready. So far though, Linux seems to be betting on PhP, Ruby and other tools more.

---

