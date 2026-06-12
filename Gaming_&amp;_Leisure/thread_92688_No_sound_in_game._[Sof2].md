---
title: "No sound in game. [Sof2]"
date: 2005-11-20
forum: Gaming &amp; Leisure
---

### Post by SkillZero on 2005-11-20
[Sof2] [Soldier of Fortune 2]
i have entered the game and it works fine and fast , but i cant hear anything.
any ideas?

---

### Post by nevelis on 2005-11-20
Are you using Cedega?

Cedega is not compatible with ALSA yet, so multiple sound streams are impossible.  Sound should just work, unless you've got ESD running, so kill it.  Also if you use KDE  apps/games, it would've started artsd so kill that too.
```
aaron@nevelis:~$ ps -A | grep esd
30696 ?        00:00:00 esd
aaron@nevelis:~$ killall esd
aaron@nevelis:~$ killall artsd (maybe?)

```

Cheers,
Aaron

---

### Post by SkillZero on 2005-11-21
[QUOTE=nevelis]Are you using Cedega?

Cedega is not compatible with ALSA yet, so multiple sound streams are impossible.  Sound should just work, unless you've got ESD running, so kill it.  Also if you use KDE  apps/games, it would've started artsd so kill that too.
```
aaron@nevelis:~$ ps -A | grep esd
30696 ?        00:00:00 esd
aaron@nevelis:~$ killall esd
aaron@nevelis:~$ killall artsd (maybe?)

```

Cheers,
Aaron[/QUOTE]

hmm k..but u need to explain few things to me:
1- what is cedega (if its an emulator so im using wine)
2- what is ALSA
3- what is ESD
4- what is KDE
tnx

---

### Post by newuser111 on 2005-11-21
cedega is a paid emulator for linux unlike free wine

ALSA = advanced linux sound architecture

ESD = enligtened sound daemon

KDE = the graphical interface for kubuntu, ubuntu uses gnome

---

