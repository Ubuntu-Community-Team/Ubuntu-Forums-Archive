---
title: "removing ubuntu"
date: 2006-07-25
forum: Desktop Environments
---

### Post by regularjordon on 2006-07-25
i was trying to remove ubuntu from my laptop, so i deleted the linux partition and the swap, and restarted my computer. now it boots to grub but wont boot to windows.

---

### Post by llamakc on 2006-07-25
Okay.

What do you want it to do? Boot to Windows? Edit grub at boot-time and specify Windows.

---

### Post by regularjordon on 2006-07-25
i want to be able to get rid of grub so i can boot to windows like normal.

---

### Post by llamakc on 2006-07-25
Okay, if you don't want to boot Windows from Grub, reinstall the Windows MBR.

---

### Post by regularjordon on 2006-07-25
ok, how do i do that?

---

### Post by llamakc on 2006-07-25
Use your recovery console or Windows media to do so.

---

### Post by regularjordon on 2006-07-25
i need more details than that.

---

### Post by Raistlin355 on 2006-07-25
Why uninstall Ubuntu?

---

### Post by llamakc on 2006-07-25
You mean to say "I request more details, please."

Your question is not Ubuntu-related. It is a "how do I boot back into Windows after removing Ubuntu and the boot-loader Grub without taking into account that Grub was handling boot procedures for Windows-question."

You need to use a Windows boot disk that has fixmbr on it. The Windows recovery console has this function. 

[SIZE=1]MS systems have a common MBR. A Dos-based system's MBR can also be restored by a NT version Windows installation CD. Any Win2k or XP installation CD will do the job. Just boot up the installation CD, choose recovery console and type the command below.[/SIZE]
 	Code:
 	[LEFT]
[COLOR=brown]**fixmbr**[/COLOR][/LEFT]

---

### Post by Thund3rstruck on 2006-07-27
it's either c:\>fixmbr or c:\>fdisk /mbr depending on the windows version

---

