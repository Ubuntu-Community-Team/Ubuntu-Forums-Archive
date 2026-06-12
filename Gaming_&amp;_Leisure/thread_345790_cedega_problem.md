---
title: "cedega problem"
date: 2007-01-24
forum: Gaming &amp; Leisure
---

### Post by L.C.D. on 2007-01-24
I've just purchased cedega from the transgaming website, i installed it with no problems, however, when i attempt to install battlefield 2142, it starts the install, then after the initial loading bar, the one that says setting up installshield wizard, i get an error saying 
"you must have administrator privileges to run setup".  
As i'm new to Ubuntu and have had very little linux experience in general i was hoping someone could help me with this.  I understand what it means, just not how to solve it.  Is there some way of running cedega with root privileges or is there some setting i need to change?

Thank you in advance for any help.

found the answer on the transgaming forums, strange they dont seem to be searched by google

---

### Post by wildseven on 2007-01-31
im very sorry if this is too late. but what that means is that you need root privelages. so try
```
gksudo cedega
```
it will prompt you for a password in gui and you should be running cedega in root mode now. i hope this works. PM me if it doesnt.

---

### Post by LebenOjanen on 2007-02-20
Actually the problem behind this is that you need to adjust your Windows Version setting with Cedega. (currently it's set to Win98 ) Open the Settings and check the General Tab for the dropdown box.  Select WinXP and it will work like a charm.

---

