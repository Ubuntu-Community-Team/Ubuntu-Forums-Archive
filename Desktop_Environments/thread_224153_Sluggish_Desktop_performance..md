---
title: "Sluggish Desktop performance."
date: 2006-07-27
forum: Desktop Environments
---

### Post by Senesence on 2006-07-27
Specs:
P4, 512MB RAM, Nvidia GeForce2 MX/MX 400.

I already got hardware acceleration working with my nvidia card, but that acceleration does not translate into regular desktop functions, like resizing windows, or scrolling.

The desktop performance is very sluggish, even though the 3d performance is lightning fast.

What could be causing this, and how do I fix it so as to have reasonably fast desktop performance?

---

### Post by allix on 2006-07-27
Try:

sudo /etc/init.d/powernowd stop

Powernowd downclocks my amd64 3000+ to 1ghz, making the GUI feel painfully slow. Don't know about P4s but its worth a try.

---

### Post by Senesence on 2006-07-27
Doesn't powernowd controll the the cpu clock speed to prevent overheating and  other troubles?

Is doing that safe?

I would also appreciate any other suggestions.

---

### Post by Lord Illidan on 2006-07-27
Run top in a terminal and post the output here. Could be an app is sucking up most of your ram.

---

### Post by Senesence on 2006-07-28
It's not a hogging issue. 

I checked sysmonitor and used top, and I noticed that there was plenty of ram available. So that's not the issue.

Anyone else have an idea of why the desktop is acting so sluggish?

---

### Post by Jhongy on 2006-07-28
I imagine its more to do with saving power (worthwhile for laptops). Your BIOS may even handle temperature monitoring for you.

Your CPU shouldn't overheat just running at stock speed, and even if it does, all it will likely do is precipitate a system crash - at which time it will have the chance to cool down again most likely. It won't spontaneoudly combust, or anything like that.

---

### Post by allix on 2006-07-28
[QUOTE=Senesence;1307591]Doesn't powernowd controll the the cpu clock speed to prevent overheating and  other troubles?[quote]

Yes, it saves battery and reduces heat on a laptop but it is useless on a desktop, except for posibly reducing fan-noise.

---

### Post by simplyw00x on 2006-07-28
In order to get an accelerated desktop:
Use XGL/AIGLX with compiz
Use blackbox
Use a non-pixmap GNOME theme

Try any or all. Also, try searching the forums before posting.

---

### Post by cptnapalm on 2006-07-28
What kernel are you using?

---

