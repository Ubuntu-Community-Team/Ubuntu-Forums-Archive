---
title: "Problem after uninstalling Wubi"
date: 2009-05-19
forum: General Help
---

### Post by cody7002002 on 2009-05-19
I uninstalled wubi but when I boot up my computer I  still get the prompt to choose microsoft xp or Ubuntu. Ubuntu does not show up in my programs list like it does when it's installed so im pretty sure it's fully uninstalled.

How do I fix this?

---

### Post by lisati on 2009-05-19
You might have to edit XP's "boot.ini" file. I'm not sure how to do that, not currently having XP on any of my machines.

---

### Post by Ms_Angel_D on 2009-05-19
sounds like you need to fix your master boot record

[LIST=1]
[*]Restart your computer with the Windows XP Setup disk in the CDROM drive.
[*]If you are prompted to press a key to start the computer from CDROM, do so quickly. Otherwise it may try to boot from the hard drive.
[*]After a few minutes, you'll see a prompt to press the R key to start the Recovery Console, go ahead and press R.
[*]When Recovery Console starts, it will prompt you to enter a number corresponding to the Windows XP installation that you need to repair. In most cases, you'll enter "1" (which will be the only choice). If you press ENTER without typing a number, Recovery Console will quit and restart your computer.
[*]Enter your Administrator password. If you don't enter the correct password, you cannot continue.
[*]At the Recovery Console command prompt, type fixmbr and then verify that you want to proceed.
[/LIST]

Your damaged MBR will be replaced with a shiny new one, and you should then be able to boot your system normally. In some cases, you may need to repair the boot sector in addition to the MBR. If your system still doesn't boot properly, repeat the steps above, but issue the fixboot command instead.

---

### Post by cody7002002 on 2009-05-19
Ah, problem there is I'm using a netbook with no optical drive and I dont have an external drive =/

---

### Post by Ms_Angel_D on 2009-05-19
Hmm well maybe somebody else will have a solution for you, I'm unsure as to how to fix it without a drive.

Sorry wish I could help more :(

---

### Post by theozzlives on 2009-05-19
go to start > run, type msconfig. You can edit your boot.ini there.

---

