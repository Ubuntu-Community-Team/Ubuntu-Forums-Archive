---
title: "Num Lock"
date: 2005-08-24
forum: Desktop Environments
---

### Post by fa2k on 2005-08-24
Hi, how can i enable num lock automatically on boot or login?

---

### Post by netrattler on 2005-08-24
[http://www.ubuntuguide.org/#numlockx](http://www.ubuntuguide.org/#numlockx)

Joe

---

### Post by Aliby on 2006-01-20
*Under KDE you don't need to install numlockx.*

[INDENT]sudo kate /etc/kde3/kdm/kdmrc[/INDENT]

*#Find the section *
[INDENT][X-*-Greeter][/INDENT]
[I]
#in this section you will find a NumLock otion 
#(or simply do a word search in the document for "NumLock")
# Change the following line from Off and un-comment it[/I]

[INDENT]NumLock=On[/INDENT]

---

