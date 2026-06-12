---
title: "[SOLVED] Windows XP freezing after dual-booting"
date: 2009-01-06
forum: General Help
---

### Post by DarkCharlie on 2009-01-06
After dual-booting Windows XP and Ubuntu, Windows has constantly been freezing randomly. It's usually after I update it, but still does it after I system restore back to before the updates.

---

### Post by oilchangeguy on 2009-01-06
> **DarkCharlie said:**
> After dual-booting Windows XP and Ubuntu, Windows has constantly been freezing randomly. It's usually after I update it, but still does it after I system restore back to before the updates.

dual booting would have no adverse effect on windows (when done properly). problems that do occur usually involve windows being deleted, not random freezing. and define freezing, is it blue screening? what is it doing?

---

### Post by 2hot6ft2 on 2009-01-06
If it's a desktop with more than 1 drive switch the cables around where they connect to the motherboard OR on the drives themselves. I had the same problem and that fixed it.

Turn the pc off and touch the case before touching anything inside to release any static electricity. And be gentle but firm pulling on one side of the connector and then the other.

---

### Post by DarkCharlie on 2009-01-06
> **oilchangeguy said:**
> dual booting would have no adverse effect on windows (when done properly). problems that do occur usually involve windows being deleted, not random freezing. and define freezing, is it blue screening? what is it doing?

It's just randomly freezing. The Start menu freezes, the windows freeze, etc. It worked fine before updating though.

---

### Post by 2hot6ft2 on 2009-01-06
> **DarkCharlie said:**
> It's just randomly freezing. The Start menu freezes, the windows freeze, etc. It worked fine before updating though.
Sounds like what mine did.

---

### Post by oilchangeguy on 2009-01-06
> **DarkCharlie said:**
> It's just randomly freezing. The Start menu freezes, the windows freeze, etc. It worked fine before updating though.

what update? service pack 3? if so just uninstall it, and disable automatic updates. you can do manual updates. by going to [www.microsoft.com](www.microsoft.com) click on microsoft updates, custom.

---

### Post by DarkCharlie on 2009-01-06
It's Service Pack 2. I didn't use Automatic Updates, I went to the Microsoft website itself to get the updates.

---

### Post by oilchangeguy on 2009-01-06
> **DarkCharlie said:**
> It's Service Pack 2. I didn't use Automatic Updates, I went to the Microsoft website itself to get the updates.

sp2 should not be causing these problems. it's a three year old update. any bugs have long since been fixed. what did you do to the computer prior to this problem(s) starting?

---

### Post by DarkCharlie on 2009-01-06
I installed Zone Alarm, but that hasn't made it freeze up before. I also installed my drivers. It's only after I go to the Microsoft website and installed all the updates that I have missed (49 of them). It freezes up after I restart my computer after that.

---

### Post by DarkCharlie on 2009-01-07
Sorry about the double post but...
I reformatted and reinstalled Windows on the partition. I have not updated, and don't really plan to unless I know why I was crashing earlier. I installed only Windows Installer 3.1 and .NET Framework 2 and everything is working fine.

---

### Post by DarkCharlie on 2009-01-07
Nevermind. After a reboot, it still freezes.

---

### Post by DarkCharlie on 2009-01-07
Quadruple post. :O
Do you think it could be GRUB? It works fine before I reinstall GRUB, but seems to freeze afterwards.
Just in case it matters, I used this method: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by oilchangeguy on 2009-01-07
> **DarkCharlie said:**
> Quadruple post. :O
Do you think it could be GRUB? It works fine before I reinstall GRUB, but seems to freeze afterwards.
Just in case it matters, I used this method: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

i'm guessing you don't know what grub is. grub (GRand Unifed Bootloader) is nothing more than the code used to start the operating system. it has nothing to do with windows freezing.

---

### Post by DarkCharlie on 2009-01-07
I know what it is, but it's just the timing of it all. It runs perfectly before reinstalling GRUB, but afterwards it does not.
This is my menu.lst also just in case.
[http://pastebin.com/m20ec6b50](http://pastebin.com/m20ec6b50)

---

### Post by oilchangeguy on 2009-01-07
> **DarkCharlie said:**
> I know what it is, but it's just the timing of it all. It runs perfectly before reinstalling GRUB, but afterwards it does not.

then remove ubuntu, and restore windows boot record. and use another computer for linux.

---

### Post by DarkCharlie on 2009-01-07
Would that be the only solution?

---

### Post by oilchangeguy on 2009-01-07
> **DarkCharlie said:**
> Would that be the only solution?

i don't know. but after two days, has a better one been presented?

---

### Post by DarkCharlie on 2009-01-09
I fixed it. It turns out vsmon.exe was taking up 100% of my memory and crashing it.

---

