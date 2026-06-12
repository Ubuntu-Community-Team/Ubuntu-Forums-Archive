---
title: "Correcting Date/Time through KDE"
date: 2005-06-12
forum: Desktop Environments
---

### Post by Gtaylor on 2005-06-12
If you right click on your clock and hit 'Adjust Date & Time', does anyone else see nothing pop up? Of course you can set date/time through the console but we shouldn't expect the average user to know how to do this.

I'm running KDE 3.4.1

---

### Post by SGC on 2005-06-12
I got the following screen, which can be accessed also from:
control center > system adminstration > date & time

---

### Post by Gtaylor on 2005-06-12
[QUOTE=SGC]I got the following screen, which can be accessed also from:
control center > system adminstration > date & time[/QUOTE]
Yeah, that's what I had got in the past, but it appears to no longer be working. Are you running KDE 3.4.1?

I tried to get to the date/time thing through the Control Center earlier to no avail also.

---

### Post by SGC on 2005-06-12
[QUOTE=Gtaylor] Are you running KDE 3.4.1?[/QUOTE]
 Yes

---

### Post by claydoh on 2005-06-12
I am also unable to edit time/date from the clock applet
I get his when trying to change date/time (see attachment) from the control panel
I can edit the time but it strays back to being 4 hours off next logout/reboot

kde 3.4.1

---

### Post by SanderAnt on 2005-06-12
I believe what you're experiencing is:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9207](https://bugzilla.ubuntu.com/show_bug.cgi?id=9207)

The work around I use is showing my timezone on the clock, but the system time remains set to UTC. I'm unclear as to where this is happening (ie KDE or ubuntu) but I was hoping it would be fixed when I upgraded to 3.4.1, but not so.

---

### Post by Apostata on 2005-06-22
Thank god I'm not the only one experiencing this...I suppose the question is this: is this a KDE 3.4.x problem (I'm using 3.4.0), or a Ubuntu problem?

It's the little things in life that drive me nuts (!) ](*,)

---

### Post by Worzel on 2005-06-23
Possible solution - try this link
[http://kudos.berlios.de/kf/kisimlar/fixes.html#fixes](http://kudos.berlios.de/kf/kisimlar/fixes.html#fixes)
HTH
Jim

---

### Post by dejitarob on 2005-06-23
Works for me. Actually it asks for my root pw. Try "sudo /usr/bin/kcmshell kde-clock.desktop --lang en_US" in the console.

---

