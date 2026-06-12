---
title: "Half-Life 2 Installation Problem [Wine 0.9.8]"
date: 2006-02-19
forum: Gaming &amp; Leisure
---

### Post by Azekriel on 2006-02-19
Hi!
When im trying to install Hl2 with like this:
wine msiexec /i /media/cdrom0/hl2.msi (Like in How-To at LinuxGamers)

When it should start installing i will get error message:
err:msi:extract_cabinet_file FDICopy failed
err:msi:ACTION_InstallFiles Unable to ready media
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Serial number of failed request:  113
  Current serial number in output stream:  132


What i should to-do get it working?

---

### Post by qb4ever on 2006-02-26
[QUOTE=Azekriel]Hi!
When im trying to install Hl2 with like this:
wine msiexec /i /media/cdrom0/hl2.msi (Like in How-To at LinuxGamers)

When it should start installing i will get error message:
err:msi:extract_cabinet_file FDICopy failed
**err:msi:ACTION_InstallFiles Unable to ready media**
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Serial number of failed request:  113
  Current serial number in output stream:  132


What i should to-do get it working?[/QUOTE]

Did you mount the cdrom?

Also try winetools:
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

---

### Post by Azekriel on 2006-03-05
Umm, this sounds noobish, but how to mount cd-rom?

---

### Post by Klejs on 2006-03-10
For ISO files you can use:
*sudo mount /path/drivename /mount/point -o loop*

But breezy should mount the CD automaticly when you put it
in.

---

### Post by Azekriel on 2006-03-19
Klejs: Its not .iso file its buyed from market, and its legal DVD.

---

### Post by GameGod on 2006-03-19
I couldn't get HL2 to install with WINE 0.9* either, but I had a valid steam account from when I used Windows and I was able to download HL2 through that...

(Also, with every release of WINE, HL2 comes closer and closer to being fully playable... Seriously, there's noticable differences between 0.9.6/7/8/9, etc... :)
So if it's not perfect right now, don't lose all hope. :))

---

### Post by GameGod on 2006-03-19
Just as a follow-up to my own post, I had a chance to try HL2 with WINE 0.9.10 today, and just as I expected, they fixed some stuff but broke some other stuff... It looks like lighting is finally working, but now there's tons of texture corruption going on, and many of the character models are still all funky.
(There should be lots of DirectDraw love coming in the next release though, so I expect the texture corruption is going to be fixed soon... I should ask around about the model stuff though...)

---

