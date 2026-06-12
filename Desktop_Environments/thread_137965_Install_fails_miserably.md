---
title: "Install fails miserably"
date: 2006-03-01
forum: Desktop Environments
---

### Post by balrog900 on 2006-03-01
When attempting to install the system all of a sudden hangs up for no reason at random parts in the install. 
Using a 1.7 ghz pentium(yeah i know this is a secondary comp)
1gb of ram
seagate 80gb hd
ge-force 5200

I have had this problem with every linux i've tried to install.

Any ideas?

---

### Post by RAOF on 2006-03-01
Suggestions:
1) Post in the "Installation and Upgrade Help" forum? :)
2) Try running the install with the "acpi=off noapci irqpoll" options?  Your motherboard probably has some quirks (read: bugs) in one or more of these subsystems.

---

### Post by aysiu on 2006-03-01
You may have a corrupted disk.

[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

---

### Post by Jason_25 on 2006-03-01
Could also be memory trouble.  Run memtest86 for a few cycles, if nothing else works.

---

### Post by balrog900 on 2006-03-01
After trying the install 21 times (yes i counted). It finnally installed. I changed nothing. It appears it was all a matter of pure luck

---

### Post by RAOF on 2006-03-01
[QUOTE=balrog900]After trying the install 21 times (yes i counted). It finnally installed. I changed nothing. It appears it was all a matter of pure luck[/QUOTE]
I smell a hardware problem.  Memtest is an **extremely** good idea :)

---

