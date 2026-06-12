---
title: "Cd autorun problem on ubuntu"
date: 2009-06-16
forum: General Help
---

### Post by arjunathakur on 2009-06-16
i have written a autorun script as below(autorun.sh):::
 
#!/bin/sh
./sysinfo
 
 
 
 
---------------
where sysinfo is a c executable file. i have saved autorun.sh and sysinfo on the cd. when i insert the cd a dialogbox comes saying media has software for autorunning ( cancel && run) ..when i click on the
run button another dialog box comes saying: "exec format error"  and sometimes " permission denied"
 
if anyone has solution to above problem please reply here...i am new to linux environment ..so please give a little detailing.....thank you...

---

### Post by arjunathakur on 2009-06-16
hi anyone there???> **arjunathakur said:**
> i have written a autorun script as below(autorun.sh):::
 
#!/bin/sh
./sysinfo
 
 
 
 
---------------
where sysinfo is a c executable file. i have saved autorun.sh and sysinfo on the cd. when i insert the cd a dialogbox comes saying media has software for autorunning ( cancel && run) ..when i click on the
run button another dialog box comes saying: "exec format error"  and sometimes " permission denied"
 
if anyone has solution to above problem please reply here...i am new to linux environment ..so please give a little detailing.....thank you...

---

### Post by mc4man on 2009-06-16
If your sysinfo can be run then dispense with the autorun.sh and instead rename sysinfo to autorun (with or without the .sh, shouldn't matter.

If it can be run than it will, if not post it (sysinfo), maybe it needs some adjustment.

I'm not to sure that ./sysinfo is correct as you have your autorun.sh now, the location is really /media/cdrom0 (or /media/cdrom1), plus there's nothing 'executing' it.

Not to long ago I set up a way for someone to autorun a script on a cd without the prompt. (in other words bypassing the 'protection' against scripts being auto run without confirmation. 
It's not posted publically but the method did involve using the location (/media/cdrom0 ) as part of an Exec=

The only determining factor was whether the script on the cd was runnable as written, not whether it would be called

---

### Post by arjunathakur on 2009-06-17
thanx for replying...


when i double click on the autorun.sh , a dialogbox comes (asking for run in terminal or display or run) i choose run in terminal , then the output of sysinfo is displayed in the terminal. but it does not work automatically when the cd is inserted. i have also made changes in the /etc/fslab  to make /media/cdrom0 exec,user....


any idiea...

---

### Post by mc4man on 2009-06-17
your not showing what "sysinfo" is 

So in lieu of that, don't know what to say, if sysinfo, whatever it is, needs to be run in a terminal than maybe try having your autorun execute it in a terminal


```
#!/bin/sh
gnome-terminal -e "./sysinfo"
```


edit
there is a ubuntu app named sysinfo that opens with sysinfo, make sure there isn't some conflict there, otherwise rename yours to sysinfo1

---

