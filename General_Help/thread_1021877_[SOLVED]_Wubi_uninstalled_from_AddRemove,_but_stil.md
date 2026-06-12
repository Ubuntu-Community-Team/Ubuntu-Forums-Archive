---
title: "[SOLVED] Wubi uninstalled from Add/Remove, but still shows bootable. help"
date: 2008-12-26
forum: General Help
---

### Post by GumpTron on 2008-12-26
I have uninstalled the Wubi from my add/remove in Vista 64 bit. Still, when I start my notebook it asks if i want to boot Ubuntu or Vista and then it doesn't work if i try to boot Ubuntu. I assume the program has been deleted but for some reason i am still asked if i want to boot it. Help!

---

### Post by namdung on 2008-12-26
[http://ubuntuforums.org/showthread.php?t=551841](http://ubuntuforums.org/showthread.php?t=551841)

[http://ubuntuforums.org/showthread.php?t=1014295](http://ubuntuforums.org/showthread.php?t=1014295)

---

### Post by GumpTron on 2008-12-26
thank you for the help Namdung. I tried the easy uninstaller but it didnt work. I think its not made for 64bit Vista. The other solutions didnt seem to help either.

---

### Post by GumpTron on 2008-12-26
!UPDATE!

i went into the registry and erased anything with Wubi or Ubuntu. Some things i could not erase and I am not sure why.

After I erased I restarted and it STILL ASKED ME IF I WANTED TO BOOT UBUNTU!. I tried to boot Ubuntu but it told me it was not possible.

cant find/issue with: ubuntu\winboot\wubildr.mbr

status: 0cx000000f

hope this helps. I really want it to just boot to Vista. :confused:

---

### Post by FXEF on 2008-12-26
GumpTron,

You have removed the Wubi Ubuntu install, it's no longer on your hard drive. The Vista BCD is still giving you the option to boot Ubuntu which is no longer installed. Vista includes a command-line tool you can use to edit the BCD; it's called Bcdedit. The syntax of the Bcdedit command is daunting, to say the least. I strongly recommend using a graphical editor for the BCD store instead. I recommend a third-party tool, VistaBootPRO, which adds a graphical interface to handle every function you can accomplish using Bcdedit and then some.

[http://www.vistabootpro.org/]("http://www.vistabootpro.org/")

This is not a free program... but neither is Vista.

---

