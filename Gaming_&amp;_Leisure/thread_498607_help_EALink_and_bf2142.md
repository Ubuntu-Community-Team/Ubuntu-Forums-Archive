---
title: "help? EALink and bf2142"
date: 2007-07-11
forum: Gaming &amp; Leisure
---

### Post by FNDII on 2007-07-11
Looking for anyone who has bf2142 running for any advice, i would assume wine works?

Also I bought the game using EALink ([http://www.ea.com/ealink/)was](http://www.ea.com/ealink/)was) wondering if this downloader program will work.

---

### Post by cogadh on 2007-07-11
Wine works to a degree. Some people have significant problems with it, others do not. See the Wine AppDB entry for it:
[http://appdb.winehq.org/appview.php?iVersionId=6637](http://appdb.winehq.org/appview.php?iVersionId=6637)

Not sure about the EALink though. If it is a Windows executable, it doesn't appear to have been tested with Wine. If it's just a browser-based app, it should still work.

---

### Post by FNDII on 2007-07-11
[http://www.ea.com/ealink](http://www.ea.com/ealink)

sorry about the link, I don't think it's browser based you have to install it.

Found this in another forum

Unfortunately I bought this game via EA's downloader (EA Link). Has anyone been able to get ea link installed? Thats whats holding me back. The EA Link installer will start to run but then die with an error about install shield. And the game requires that EA link be running in order to run the game.


no one posted back

---

### Post by cogadh on 2007-07-11
I can get the install to nearly complete, but it ends up complaining about a missing DLL. I'll play around with it some more and see if I can work past it. I'll post back if/when I get some better results.

---

### Post by cogadh on 2007-07-11
Well, no luck with installing the EA Link software. The DLL it was complaining about was advapi32.dll, which is one of the DLLs that you shouldn't override in Wine (it makes Wine unusable). If the game requires EA Link to be running in order to launch, I don't think you'll be able to play it in Ubuntu. Maybe someone else can find a way to get it installed and running, but I'm stumped. :(

---

### Post by FNDII on 2007-07-21
I was thinking,

Can i log on to windows and DL/install the game from EAlink and then drag the files over to linux? (like they said you can do in the wow guide?)

---

### Post by cogadh on 2007-07-21
You can try that, it sometimes works. The only way it might cause a problem is if the application or the game need to read specific entries from the registry that are made during the install process. It's definitely worth trying, though.

---

