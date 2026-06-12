---
title: "Gnome-system-monitor"
date: 2008-03-12
forum: Desktop Environments
---

### Post by anathema415 on 2008-03-12
When I try to run gnome-system-monitor I get this:

> gnome-system-monitor: symbol lookup error: gnome-system-monitor: undefined symbol: _ZN7pcrecpp6no_argE 

I googled the error and it seems to be a problem with pcre (which I had updated myself foolishly). I tried removing the version I installed and reinstalling the version ubuntu comes with via synaptic. 

I don't want to re-install ubuntu if I can avoid it. Any suggestions?

---

### Post by anathema415 on 2008-03-12
bump

---

### Post by anathema415 on 2008-03-12
I downgraded from pcre 7.6 to 7.5 and now get this error

> gnome-system-monitor: symbol lookup error: gnome-system-monitor: undefined symbol: _ZN7pcrecpp2RE4InitEPKcPKNS_10RE_OptionsE

How can I fix this?

---

### Post by anathema415 on 2008-03-13
There's got to be somebody who can help me

---

### Post by Mr_Congeniality on 2008-04-13
I'm having the same problem too and I can't figure what the hell is wrong.

---

### Post by Mr_Congeniality on 2008-04-13
Wait...I think I might have a resolution to this issue.

I'm betting that you installed pcre 7.6.  For some odd reason it's bugged out or something, there's no explaining why it hasn't been fixed yet.  I tried someone's advice in downgrading to pcre7.4 by compiling it from source but that only messed it up and gave me another unknown symbol error, but with a differen't symbol name.

So what you should do, is download the 7.4 source instead, ./configure it again, do sudo make and sudo make install, then do sudo make uninstall, and just in case, reinstall the pcre versions provided in the synaptics package manager.  Also check for any broken packages just in case.  I did this, and everything is back up and going.

Deleting files and folders related or directly involving pcre isn't going to cut the cake and will frak over your system possibly even more.  You need to make sure you do "sudo make uninstall".

This worked just fine for me.

---

