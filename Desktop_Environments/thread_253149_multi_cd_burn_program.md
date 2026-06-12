---
title: "multi cd burn program"
date: 2006-09-07
forum: Desktop Environments
---

### Post by domonics on 2006-09-07
Hey all, was wondering if there is a cd burning program out there that can burn 2 or more cd's simultaneously. When i used to use XP:D , nero would be able to burn up to 4 cd's at the same time. Just hope that i can do it with a native program rather than having to install nero using wine.

Thanks

---

### Post by orb9220 on 2006-09-07
Nero will not run in wine. There is a crude linux version of nero version 2.xxx

---

### Post by domonics on 2006-09-08
well right now i have installed nero linux wich seems to work in burning cd's one at a time. But what i am looking for is a program that can burn multiple cd's at once, at least two.

---

### Post by az on 2006-09-08
Screw proprietary apps!

[http://packages.ubuntu.com/dapper/utils/cdcontrol](http://packages.ubuntu.com/dapper/utils/cdcontrol)

QUOTE:
CDcontrol is a parallel CD burner program. It allow you write to a unlimited number or CD writers (IDE and SCSI) at once time. The CDcontrol is the first burning system of that type that I know for *nix operating system and it's all under GPL license. 

Some of it features are better than commercial systems that I've hear about (and fully support CD images and all data type supported by cdrecord program), one of these features is the separated control of each recorder once the recording is started (avoid problems due a fail or speed problem in other writers). 

The CDcontrol itself has a daily production report for each writer and fails of writing, in cases of more serious errors, a technical report is also written (it content is a full cdrecord output for that writer, plus the time when it happens). 

Other interesting feature is the automatic calculation of copies, enabling only the writers requested to complete the number and skipping all that are disabled. 

The CDcontrol interface is very simple and dialog based, simple type "cdcontrol" and enjoy.

---

