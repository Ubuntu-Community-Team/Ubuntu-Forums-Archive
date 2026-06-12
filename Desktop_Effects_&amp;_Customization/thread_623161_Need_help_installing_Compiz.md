---
title: "Need help installing Compiz"
date: 2007-11-25
forum: Desktop Effects &amp; Customization
---

### Post by uBrendon on 2007-11-25
K guys I'm completely new to linux/Ubuntu, I have the compiz un compacted or whatever and I don't know where to go from here, I checked youtube, google, yahoo etc even searched on here. The simple question is How do I install compiz-fuzion?

---

### Post by Ub1476 on 2007-11-25
If you're running the latest release of Ubuntu, Compiz-Fusion is already installed on it. Go to System>Preferences>Appearance>Visual Effects.

If you want more advanced effects, install compizconfig-settings-manager.

```
sudo apt-get install compizconfig-settings-manager
```

Or search for it in Synaptic.

---

### Post by uBrendon on 2007-11-25
The latest release is 7.10 right? That's what I have. When I typed that in terminal this happened, help. and thanks in advance

brendon@Brendon-laptop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for brendon:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
brendon@Brendon-laptop:~$

---

### Post by Ub1476 on 2007-11-25
Yes.

Go into System>Administration>Software Sources and check:

[LIST]
[*]main
[*]universe
[*]restricted
[*]multiverse
[/LIST]

---

### Post by uBrendon on 2007-11-25
Check what? (Sorry I'm new)

EDIT: Never mind you edited it now what do I do?

---

### Post by fineas on 2007-11-25
First, go System>Administration>Synaptic package manager.In menu bar, go to Settings>Repositories.There, in the first tab , check 

main
universe
restricted
multiverse

Then,search again for the compizconfig-settings-manager in synaptic.

---

### Post by DutyDuty on 2007-11-25
Once you install that, run a quick```
ccsm --replace
and
compiz --replace &
```

---

### Post by uBrendon on 2007-11-25
What does that do?

---

### Post by FuturePilot on 2007-11-25
> **DutyDuty said:**
> Once you install that, run a quick```
ccsm --replace
and
compiz --replace &
```

> **uBrendon said:**
> What does that do?

I'm not sure what the first one does, but the second one will run Compiz. But what version of Ubuntu are you running? 7.10 has most of Compiz Fusion already installed. Just make sure you have have the 3D driver installed. System>Administration>Restricted Driver Manager

---

### Post by uBrendon on 2007-11-26
I didn't have to install any drivers and I got it working. Loving the Cube.. =) Thanks everyone! Oh and im running 7.10

---

### Post by FuturePilot on 2007-11-26
> **uBrendon said:**
> I didn't have to install any drivers and I got it working. Loving the Cube.. =) Thanks everyone! Oh and im running 7.10

Awesome! Enjoy :guitar:

---

### Post by DutyDuty on 2007-11-26
[QUOTE=FuturePilot]I'm not sure what the first one does,[/QUOTE]

ccsm --replace will restart the ccsm, useful when installing new plugins or just a good thing to do to make sure everything is actively working.

EDIT: This thread should be marked solved.

---

