---
title: "No window borders in XGL/Beryl"
date: 2006-11-13
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2006-11-13
Hey Im using Beryl/XGL on a radeon x1600pro with the fglrx drivers. I have everything set up but when I load the beryl window manager, my window borders dissapear and it seems that none of the effects are enabled. Does anyone know how to fix this? :D

---

### Post by DimitrisC on 2006-11-13
Had the same problem and searching the forums i found something that worked for me so it may work for you.

Add emerald --replace in your startup under sessions and give it a try. Hope it helps!

---

### Post by WalmartSniperLX on 2006-11-14
> **DimitrisC said:**
> Had the same problem and searching the forums i found something that worked for me so it may work for you.

Add emerald --replace in your startup under sessions and give it a try. Hope it helps!

wait in what file :D

EDIT: Im in KDE so I I dont know where that is :S

---

### Post by d3v1ant_0n3 on 2006-11-14
In KDE I *think* its in Kcontrol>KDE Resources>Sessions.

I haven't got KDE to confirm this tho, and I might be very wrong. My memory sucks. You might have to randomly flick around the kcontrol menus for a while:p

*edit* try running the command in terminal first to confirm if it works.

---

### Post by WalmartSniperLX on 2006-11-14
> **d3v1ant_0n3 said:**
> In KDE I *think* its in Kcontrol>KDE Resources>Sessions.

I haven't got KDE to confirm this tho, and I might be very wrong. My memory sucks. You might have to randomly flick around the kcontrol menus for a while:p

*edit* try running the command in terminal first to confirm if it works.

:( Im afraid im still a noob when it comes to this. Never did it before ](*,)  Where is Kcontrol? What would be the command. Im sorry if Im a little annoying :mrgreen:

---

### Post by chriscando on 2006-11-14
I get that sometimes and can easily fix it. Start beryl-manager and click on the red diamond that appears in the task tray. Goto select window manager and verify that it is on beryl, if so click on refresh window manager. That does it for me, hopefully you too.

---

### Post by WalmartSniperLX on 2006-11-14
> **chriscando said:**
> I get that sometimes and can easily fix it. Start beryl-manager and click on the red diamond that appears in the task tray. Goto select window manager and verify that it is on beryl, if so click on refresh window manager. That does it for me, hopefully you too.

:S 

```

Failed to open device
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

```

Do I *need* Nvidia? Im sure Ive seen people saying it worked with ati fglrx. 

Anyone know what this means? I get this when reloading the win manager beryl with beryl-manager

---

### Post by chriscando on 2006-11-14
try running beryl-xgl first.

---

### Post by WalmartSniperLX on 2006-11-14
> **chriscando said:**
> try running beryl-xgl first.

```

patrick@patrick-desktop:~$ beryl-xgl
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl-xgl: No composite extension

```

It says XGL absent :S and no composite ext.

should i enable composite extension in xorg.conf?

---

### Post by WalmartSniperLX on 2006-11-14
Nvm I did that and it just messed it up more. I have it disabled again ](*,)

---

