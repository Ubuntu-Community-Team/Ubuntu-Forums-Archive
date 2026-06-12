---
title: "Random &quot;keyboard&quot; freezes in Gutsy"
date: 2007-10-24
forum: Desktop Environments
---

### Post by tony11235 on 2007-10-24
So I'll be in typing in Pidgin, Evolution, or Firefox, whatever, and all of a sudden I can't type in the given window that I'm in. It doesn't totally freeze because I can click on tabs, and the alike, and it still will function, BUT I can't enter text. I have to like close the application and start it again. This is happening on ALL three of my machines which I'm running Gutsy on. They are all up to date. This is getting really really frustrating, especially when in the middle of a pidgin window conversation.

---

### Post by harsono on 2007-10-26
i'm having the same problem here
but strangely the keyboard freezes only on specific apps
i.e. File Browser, vncviewer, etc
but not on gnome-terminal or firefox

---

### Post by huangja on 2007-10-26
I am having this problem too, when I use pidgin, I would have to close it and reopen it to get it to work. It seems like a bug in a lot of systems, hopefully, they'll put out a fix soon.

---

### Post by tony11235 on 2007-11-15
Well I'm glad to know it's not just me now. I posted a report about it on launchpad.

---

### Post by genki_genki on 2008-01-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104)  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Mine is same keyboard-freezing problem, but affecting also gnome-terminal and firefox.

I'm using SCIM for Japanese input. Googling I found a input freezing problem reported in Bug #66104  by  Wenzhuo Zhang. [https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104) describes the problem. Also quotes that SCIM is now merged into Gutsy and still presenting the same freezing problem. 

The report from Wenzhuo also presents a simple workaround that helped me:

  Set /FrontEnd/X11/Dynamic = true  in ~/.scim/config , you have to re-login.

(also see last comment from Juerd  [https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104/comments/40](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104/comments/40)  , though I'm not sure about the need of making the file immutable)

There are also workaround quotes for DeadKeys for some European keyboards in same report.

Hope this helps.

---

