---
title: "ATI dual head makes full screen games crash?"
date: 2005-04-17
forum: Gaming &amp; Leisure
---

### Post by shakin on 2005-04-17
I used fglrxconfig to try both big desktop and dual head configurations for my 9800 Pro and in both cases ALL games fail to load in full screen (native and cedega).

After configuring xorg.conf for single head mode the games work really well except for Enemy Territory, which sends me back to the login screen.

I'm just curious if anybody else has experienced this behaviour with their ATI card. Sounds to me like a driver bug.

My system is an Athlon XP 3200 with the 128MB 9800 Pro and 768MB RAM.

---

### Post by Bug on 2005-04-17
ATI drivers are really bad in Linux, I'd think it's that. 

But I just dragged another monitor over to my desk to see if I can get this to work, I'll let you know. I've got a 9800SE 128MB card, one DVI LCD and one VGA CRT monitor.

Adam

---

### Post by shakin on 2005-04-17
[QUOTE=Bug]ATI drivers are really bad in Linux, I'd think it's that. 

But I just dragged another monitor over to my desk to see if I can get this to work, I'll let you know. I've got a 9800SE 128MB card, one DVI LCD and one VGA CRT monitor.

Adam[/QUOTE]

Great. Just beware that fglrx will force your DVI to be the first monitor whether you're in dual head or not. The Ubuntu installer setup the VGA out as the first monitor, so that part kind of screwed me up at first :)

---

### Post by Bug on 2005-04-20
[QUOTE=shakin]Great. Just beware that fglrx will force your DVI to be the first monitor whether you're in dual head or not. The Ubuntu installer setup the VGA out as the first monitor, so that part kind of screwed me up at first :)[/QUOTE]
 Not working... But it does flicker, so either the monitor is bad or it could be my sync rate. Sorry I haven't had time to dig deeper, but I want it to work so I'm going to keep trying.

Adam

---

