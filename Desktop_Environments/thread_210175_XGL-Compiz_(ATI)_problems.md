---
title: "XGL-Compiz (ATI) problems"
date: 2006-07-06
forum: Desktop Environments
---

### Post by mat69 on 2006-07-06
I've an ATI X1600 AGP.

OK, I installed compiz (packages from here: [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) ) and xgl (following that HowTo: [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) )
Now whenever I start a programm you can't see anything, you have to mark the text in browsers to see it and hover over buttons to see them, otherwise you simply see only the desktop (background).

Is there a way to solve this problem and is there a way to run compiz with the X1600 or are the "Supported Hardware" named in the HowTo really the only hardware XGL will work on?

Thank you for reading and sorry for the probably stupid questions.
Matthias

---

### Post by krazyd on 2006-07-06
I've got an ATI Radeon X1600 on my laptop which works fine with Xgl / Compiz.

[http://www.compiz.net/viewtopic.php?pid=11734](http://www.compiz.net/viewtopic.php?pid=11734) is the guide i used. I'm currently using drivers:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

---

### Post by mat69 on 2006-07-06
Thank you for your answer, can you please post the ways (Howtos or whatever) how you installed fxglr and xgl as well, so that I can "copy" the way you did it, reducing the risk of errors? That would be fantastic.

---

### Post by krazyd on 2006-07-07
Oops! Sorry, the link I gave was the wrong one! I used this installation guide to install Xgl / Compiz: [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

I then used this guide to get the configuration applet working: [http://www.compiz.net/viewtopic.php?pid=11734](http://www.compiz.net/viewtopic.php?pid=11734)

Just in case, here's how to install the ATI proprietry drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

By the way, most of this stuff can be found from links on this site: [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

---

### Post by mat69 on 2006-07-07
Hello I installed fglrx but I am running into problems (see screenshot).

```

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.5879 (8.26.18)

```

I added my xorg.conf and the result of "dmesg|grep fglrx" and xorg.0.log as attachment.

Sorry for this short post, but it is hard to post with that problem.

Btw. thank you for all the links!

Edit: If I change to another Virtual Desktop and then back everything is rendered fine as long as I do not scroll (PgDown and PgUp works) or move the windows.
Without "Option "XaaNoOffscreenPixmaps"" the effects are even worse than shown in the screenshot

---

