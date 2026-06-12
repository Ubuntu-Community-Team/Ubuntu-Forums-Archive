---
title: "Can't format floppies"
date: 2005-06-22
forum: Desktop Environments
---

### Post by keithp on 2005-06-22
I can't format floppies with KUbuntu, using Kfloppy.

If I set it to auto select, I get the error message "Unexpected density number 0".

If I set it to 3.5inches and 144 Mb, I get the error message "Cannot access /dev/fd0u1440. Make sure that the device exists and you have write permsiions to it".

There is a device fd0 (without the u1440 part) which is owned by root and has floppy as the group. I am a member of the floppy group.

I have tried formatting after having done a Sudo to root. Still the same error messages.

I can format floppies with Ubuntu, using the Gnome floppy format program (can't remember its name!). it's just in KDE that I can't.  

Any ideas, please?

Many thanks

Keith

---

### Post by Takis on 2005-06-22
I don't know what the problem is, but if you like using KFloppy we can cheat a little bit:
```
$ sudo ln -s /dev/fd0 /dev/fd0u1440
```

---

### Post by keithp on 2005-06-23
Thanks for your help.

Entering the script does cure the problem, but only for that session.

After I have booted again, if I want to format any floppies, I have to type the link again. It's a bit of a nuisence, especially as other distros I have tried, don't have this problem.

Perhaps there is another formatting program which I can use, which is OK. I'll have a look round.

Cheers

Keith

---

### Post by shakin on 2005-06-23
You can use the Gnome program in KDE.

---

### Post by Takis on 2005-06-23
[QUOTE=keithp]Entering the script does cure the problem, but only for that session.[/QUOTE]
Oh yeah silly me - /dev is a tmpfs, it's lost when you reboot.

Okay new attempt: edit your KMenu entry for KFloppy (right-click on the menu entry and select edit) and in the 'command' textbox, append: '<space>/dev/fd0' - where <space> means ' '.

---

