---
title: "Incorrect scaling, multiple displays (19.10)"
date: 2020-04-22
forum: Desktop Environments
---

### Post by hast4656 on 2020-04-22
[COLOR=#242729][FONT=Arial]I've been using Ubuntu Mate 19.10 for at least a half year, and everything was perfect until 1 week ago I updated all packages (apt update && apt upgrade). I suppose that it was some big update, because a lot of packages got new versions, my display drivers were updated, after restart I had to enroll mok before booting the system, etc.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]But here comes the problem: after this update a lot of interface items became much smaller. I can see that running application icons on my top bar became smaller, their number was increased and the fonts became much thinner. And while for the most applications nothing really changed (maybe fonts became a very little bit smaller), some applications became impossible to use. For example all elements and fonts in my JetBrains IDEs became so small I can't even read them at all. I contacted jetbrains support, but it looks like it's some kind of a system issue.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Worth to mention: I use laptop (HP envy 15.6", 15.6", 1920x1080) and an external Dell monitor (27", 1920x1080). If I unplug my external display and then reboot - everything becomes normal. Moreover, if I plug in my external monitor after system is booted - everything is also OK.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Since I didn't change any configuration, I'm 100% sure that the last update was the reason of the issue. That's why I'm looking for a way to restore my previous state.[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-04-22
> [COLOR=#242729][FONT=Arial]I had to enroll mok before booting the system, etc.[/FONT][/COLOR]

That means you have Secure Boot enabled and are using unsigned drivers (Nvidia?).

---

### Post by hast4656 on 2020-04-22
Actually I have no idea what enroll mock means, what is secure boot and what drivers I use. Sorry :D  I'm not really into linux, but I have to use it now, so I could miss something.

But yes, Nvidia. Anyway, they had been working fine for months before I just run apt update + upgrade, that's all... What can I check / look at, so you can help me?

---

### Post by CelticWarrior on 2020-04-22
You can open Additional Drivers and check what drivers are in use, for starters.
If you have Nvidia Graphics you want to use proprietary drivers in order to have it work at the full performance (why else you want a powerful graphics if not to use it?). The default open-source drivers in Debian/Ubuntu is likely not enough.
This has little to nothing to do with Linux, it has to do with your hardware and what it needs regardless of the OS.
Also Secure Boot is a UEFI("BIOS") feature, nothing to do with the OS. Knowing about it is part of the current computer literacy required to install and manage OSes. It's often recommended to disable it, for convenience.

---

### Post by hast4656 on 2020-04-22
This is my drivers settings. As far as I remember they weren't changed for a while. I also tried to turn off secure boot in bios setup, but nothing changed.
[IMG]https://i.imgur.com/S8g3yIW.png[/IMG]

---

### Post by hast4656 on 2020-04-24
Any ideas?

---

### Post by hast4656 on 2020-04-28
The problem hasn't gone even after I updated to 20.04 LTS and installed last Nvidia proprietary drivers (440). So I literally can't using my laptop with ubuntu anymore and no one can help me.

---

### Post by mörgæs on 2020-04-29
> **hast4656 said:**
> ...and no one can help me.

Really? OK, then you have to help yourself. 
You can do so by trying to install 20.04 in a clean install with the monitor detached.

---

