---
title: "wine homeworld2 error:fixme:dxdiag:IDxDiagContainerImpl_AddProp"
date: 2007-04-10
forum: Gaming &amp; Leisure
---

### Post by Dan_472 on 2007-04-10
I'm trying to play homeworld2_demo.   ([http://www.homeworld2.com/downloads.jsp](http://www.homeworld2.com/downloads.jsp))       Using Wine 0.9.9

The game seemed to install OK, but when I try to execute Release.exe (which I think should start the game) in the terminal I get about a hundred error messages that all start the same way, with the numbers changing at the end:


fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7fd4b6f8, L"dwDirectXVersionMajor", 0x7fb9fd3c)

What should I do?

Thank you

---

### Post by hikaricore on 2007-04-10
It doesn't look like you'll have much luck with either the demo nor the retail version of the game.

Sorry to say, every report in the application database is Garbage, which means serious
problems attempting to run the game under linux using WINE.

[http://appdb.winehq.org/appview.php?iAppId=2616](http://appdb.winehq.org/appview.php?iAppId=2616)

---

### Post by Dan_472 on 2007-04-11
My mistake!  I was looking at this url:  [http://appdb.winehq.org/appview.php?iVersionId=573&iTestingId=3082](http://appdb.winehq.org/appview.php?iVersionId=573&iTestingId=3082)

which is for Homeworld 1.05  and is rated as working well under wine.      But I see what I downloaded from Sierra was Homeworld 2 .

So I'm gonna try [http://www.fileplanet.com/filelist.aspx?s=56511&v=0](http://www.fileplanet.com/filelist.aspx?s=56511&v=0)      and      [http://www.fileplanet.com/40576/download/Homeworld-v1.05](http://www.fileplanet.com/40576/download/Homeworld-v1.05)

update:   OK,  plain Homeworld works great!   haven't tried the version 1.05 patch, but I expect it will work fine also.

---

