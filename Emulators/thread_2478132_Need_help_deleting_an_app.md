---
title: "Need help deleting an app"
date: 2022-08-17
forum: Emulators
---

### Post by jonfisher on 2022-08-17
Need help deleting an emulator app.  Didn't install it with synaptic (or Ubuntu software center)

It's called "FS-UAE Launcher"

---

### Post by ActionParsnip on 2022-08-17
What is the output of:
```

dpkg -l | grep uae

```
This may give clues

---

### Post by howefield on 2022-08-17
Thread moved to the "*Emulators*" forum.

---

### Post by jonfisher on 2022-08-17
> **ActionParsnip said:**
> What is the output of:
```

dpkg -l | grep uae

```
This may give clues

Interestingly, this command line does nothing 
(?)

---

### Post by ActionParsnip on 2022-08-17
OK try
```

grep -i UAE /usr/share/applications/*

```
What is the output?

---

### Post by #&amp;thj^% on 2022-08-17
Without knowing how you installed it, use this and return the output back in your reply:
```
sudo apt-get purge --auto-remove fs-uae-launcher
Architecture: all
Version: 3.0.2+dfsg-2
```
If that don't work you'll have to point us to the link used to install it..

---

### Post by jonfisher on 2022-08-17
> **ActionParsnip said:**
> OK try
```

grep -i UAE /usr/share/applications/*

```
What is the output?

Thanks again & again no output

```

michael@michael-HP-EliteDesk-800-G1-SFF:~$ grep -i UAE /usr/share/applications/*
michael@michael-HP-EliteDesk-800-G1-SFF:~$ grep -i UAE /usr/share/applications/*
michael@michael-HP-EliteDesk-800-G1-SFF:~$ 


```

---

### Post by jonfisher on 2022-08-17
> **1fallen said:**
> Without knowing how you installed it, use this and return the output back in your reply:
```
sudo apt-get purge --auto-remove fs-uae-launcher
Architecture: all
Version: 3.0.2+dfsg-2
```
If that don't work you'll have to point us to the link used to install it..

Thanks & the output is:

```

michael@michael-HP-EliteDesk-800-G1-SFF:~$ sudo apt-get purge --auto-remove fs-uae-launcher
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'fs-uae-launcher' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
michael@michael-HP-EliteDesk-800-G1-SFF:~$ 

```

---

### Post by #&amp;thj^% on 2022-08-17
Great thanks for that, do you have the instructions you followed to install it?
Or check this for me please:
```
flatpak list
```

---

### Post by jonfisher on 2022-08-17
Unfortunately I don't recall how I installed it...
Perhaps I should look in one of the directories to try and figure out exactly where it is?  Where are most programs/apps installed at ?  I can't find it in usr/bin

---

### Post by #&amp;thj^% on 2022-08-17
This may be one of those hard learned lessons of installing apps from a third party site.
Important: If your compiling to install, first make sure it is well documented and most importantly that there is a Un-install how to included.

---

### Post by SeijiSensei on 2022-08-17
Try using "locate uae". If you get the reply that plocate (or mlocate or something similar) is not install, follow the instructions provided, then try again.

My guess is you installed the binary from a tar or zip file.

---

### Post by TheFu on 2022-08-17
> **jonfisher said:**
> Unfortunately I don't recall how I installed it...
Perhaps I should look in one of the directories to try and figure out exactly where it is?  Where are most programs/apps installed at ?  I can't find it in usr/bin

The general rule is to remove a program, you have to use the same tool you used to install it to uninstall it.  If it isn't in APT or a snap or a flatpak, then you can almost certainly just delete the files.  Many programs come with an install script. That script might have a de-install option too or not.  The README for the software should have any install/uninstall instructions. If there aren't any and it isn't APT, snap, flatpak, just remove it and all the pieces. 

If the program has a menu, then there is a .desktop file somewhere.
If the program can be run without specifying the exact, full, path to the program, then it is in your PATH and "which {program-name}" will find it.

Be certain you have a good system backup, before removing it, unless you 100% know it isn't a critical application for other tools on the box.

---

### Post by jonfisher on 2022-08-17
Was able to remove it using:

"[FONT=monospace]sudo snap remove fsuae[/FONT]"

Thanks all for the help and marking this as solved.

---

