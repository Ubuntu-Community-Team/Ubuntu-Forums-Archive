---
title: "XDMPC question"
date: 2008-03-05
forum: Desktop Environments
---

### Post by gnurph on 2008-03-05
I've searched around and can't find an answer to what I think is a simple question (if this is the wrong forum, I apologize in advance, too):

I reboot my Ubuntu 7.10 system and want to log in remotely using XDMPC.  When I do so, using Xming (yes, the Windows version), I get the login screen, I appear to log in - but all I get is the tan colored Ubuntu background.

Do I already have to be logged into a box INITIALLY to be able to log in using XDMPC?  That doesn't sound like something that should have to be done, but I'm otherwise at a loss.

Thanks,

Lee

---

### Post by kevinatkins on 2008-03-05
Hi,

I think XDMCP is broken in Ubuntu 7.10.... I've experienced the same problem, yet in earlier versions, it worked great.

---

### Post by gnurph on 2008-03-05
Interestingly enough, I actually managed to do it once...

then I couldn't any longer.

Then I went to the computer in question, logged in there...and got the same blank tan screen.  

Whoa.  Perhaps it's time for VNC?

---

### Post by shockwaver on 2008-03-06
No, you shouldn't need to be logged in to use XDMCP. I'm using it now with my 7.10 install (I use it every day). Not sure if you're using the gnome greeter to log in (default with ubuntu) and if you are I'd suggest making sure that the remote interface is set to plain (System->Administration-Login Window. Click the remote tab, and choose Style: Plain.) - That was a problem I was having for -ages-. Also, are you on a local network? Wireless? I've found that with wireless B running at ~10Mbs I couldn't log in fully to the desktop.. wasn't till I upgraded the connection to G ~54Mbs that I could get a desktop that was responsive. I suppose the lag was making it very hard to sync. 

If low bandwidth/high lag is the culpret (IE, connecting both machines to wired fixes it) you can run individual applications through Xming and using a program like PuTTy. If you like, I can post a how-to on SSH X forwarding via PuTTy with Xming.

---

### Post by snelo on 2008-05-17
You need to disable ESD in your sound preferences... don't know why... but I had the same problem and after I while I discovered that this was the fix that others had used.

---

