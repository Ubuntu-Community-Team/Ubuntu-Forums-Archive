---
title: "Kubuntu messes XP's clock"
date: 2005-08-03
forum: Desktop Environments
---

### Post by Owdy on 2005-08-03
After instllations, everytime i start windows, its time is wrong. Syncronising helps, but i dont wanna do that everytime.

---

### Post by ltmon on 2005-08-03
I think Linux stores the system clock in UTC, and then calculates your time based on your timezone info wheras Windows stores the system clock at local time.

To fix:

Edit /etc/sysconfig/clock file and set the line "UTC=true" to "UTC=false", then reboot.

I think this screws up your time if Ubuntu ever crashes.  If Ubuntu crashes, boot into Windows to fix up the time.

Cheers,

L.

---

### Post by Owdy on 2005-08-03
/etc/sysconfig/ folder doesnt exist.

---

### Post by f1dave on 2005-08-03
Not to imply you haven't tried this, but are you using sudo to try and open the folder?

EDIT: Wait, you're right... I should check before answering.  :roll:

---

### Post by Firetech on 2005-08-03
The file is /etc/default/rcS, and the syntax is yes/no rather than true/false.
There is no need to reboot after changing the value, it will be done when you exit linux the next time.

Linux's software clock is completely independent of the hardware clock, it just uses it to get the time on boot, and set the time to it on shutdown (to save it). If the variable UTC is yes then, it will add/subtract  from the time to make it UTC time, if the variable is no, it will save the clock as is.
Windows on the other hand, takes the time directly from the hardware clock at all times (AFAIK). If the UTC value in linux is yes then, this will screw the clock up (get it out of sync).

---

### Post by spectra1 on 2005-08-12
Do I enter his command in the terminal window. If so I tried this and it said permission denied

---

### Post by Mechsus on 2005-08-12
[QUOTE="Owdy"]After instllations, everytime i start windows, its time is wrong. Syncronising helps, but i dont wanna do that everytime.[/QUOTE]

Red Hat Linux 9 messes up Win XP's clock too.

---

### Post by Owdy on 2005-08-12
[QUOTE=Mechsus]Red Hat Linux 9 messes up Win XP's clock too.[/QUOTE]
 That Firetech's tip worked perfectly.

---

### Post by brannolte on 2005-08-17
[QUOTE=spectra1]Do I enter his command in the terminal window. If so I tried this and it said permission denied[/QUOTE]

@spectra1
hi,

after starting the teminal use "sudo /usr/bin/kate YOURFILE" to edit the file with root-rights.

Greets bra

---

### Post by thomax on 2005-08-17
[QUOTE=Firetech]The file is /etc/default/rcS, and the syntax is yes/no rather than true/false.
There is no need to reboot after changing the value, it will be done when you exit linux the next time.

Linux's software clock is completely independent of the hardware clock, it just uses it to get the time on boot, and set the time to it on shutdown (to save it). If the variable UTC is yes then, it will add/subtract  from the time to make it UTC time, if the variable is no, it will save the clock as is.
Windows on the other hand, takes the time directly from the hardware clock at all times (AFAIK). If the UTC value in linux is yes then, this will screw the clock up (get it out of sync).[/QUOTE]

Thanx man, your trick worked perfectly

---

### Post by rstana on 2005-08-19
[QUOTE=brannolte]@spectra1
hi,

after starting the teminal use "sudo /usr/bin/kate YOURFILE" to edit the file with root-rights.

Greets bra[/QUOTE]

you can right-click the file and choose Actions - Edit As Root it will prompt you for password and there you go... no need to start terminal even

---

