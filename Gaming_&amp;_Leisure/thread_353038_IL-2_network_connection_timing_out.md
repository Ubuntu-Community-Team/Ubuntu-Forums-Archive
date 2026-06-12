---
title: "IL-2 network connection timing out?"
date: 2007-02-04
forum: Gaming &amp; Leisure
---

### Post by Saubazi on 2007-02-04
I have IL-2 up and running but everytime I try to connect on online server 
I get a time-out. I don't think I have any firewall active or anything (how can I check).
The game works on windows boot so I think it is not in the router configuration either
since there are no special allowances. So what can I try. I know it should be possible to
get it working. This is my last hurdle and the last thread that holds my windows partition
alive...

---

### Post by tht00 on 2007-02-05
> **Saubazi said:**
> I have IL-2 up and running but everytime I try to connect on online server 
I get a time-out. I don't think I have any firewall active or anything (how can I check).
The game works on windows boot so I think it is not in the router configuration either
since there are no special allowances. So what can I try. I know it should be possible to
get it working. This is my last hurdle and the last thread that holds my windows partition
alive...

I'm curious -- what did you use to get IL-2 working and what version of IL-2?

---

### Post by Saubazi on 2007-02-06
Hmm...

The main problem is the installation (mainly the CD-change in it) so a safe bet is to copy the installation directory from windows partition and change the rights with chmod -R u+wr <IL-2 directory> - a mean to bypass CD-check is required (rts.dll)

I am not 100% sure if a DVD installation of the whole product might work on linux - it is possible I think.

The next question is wine version - majority work - I use 0.9.29 since 0.9.30 seems to give me headaches with my joysticks. 

Wine version needs to be set to windows 2000

For joysticks it is probably necessary to softlink sticks from /dev/input/js* to /dev/js*

That's about that. I'd say any version of IL-2 will run.

---

