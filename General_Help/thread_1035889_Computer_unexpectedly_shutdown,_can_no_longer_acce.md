---
title: "Computer unexpectedly shutdown, can no longer access kubuntu,"
date: 2009-01-10
forum: General Help
---

### Post by dfk789 on 2009-01-10
I spent the most part of last night installing kubuntu through wubi. Worked great, spent lots of time configuring it, also great. I put some music on, and go to sleep. I wake up in the morning, my is off, I boot up to try and get into kubuntu, I get an error saying grub can't find the boot file, none of the options seem to work, so I decide to go uninstall it through windows to claim my hdd space back. 

Here's where the problem starts, windows says I do not have wubi installed. I go into the ubuntu directory and run the uninstaller from there. It seems to work though there is a folder left in there called disk. Which I think is my hdd space. I'd like to get that back so I can install wubi to the same place again. Rather than having it take up even more space. Can anyone help me here?
The folder itself says "this file/directory is corrupted or unreadable.

Edit: So what I'm doing at the moment is reinstalling wubi, it's downloading again at the moment, about 20 minutes left. I plan for it to install in windows, then restart, whilst it's loading into kubuntu rather than having it install I'll push ctrl+alt+backspace and that'll bring me into a live cd version. I'll see if i can access the old disk folder and if i can delete it from there. Which shall hopefully get me my space back. Wish myself luck.

Edit:Ok, well that didn't work as planned but helped none the less. I have managed to remove what I had of wubi on my system. All disk folders gone. This was done by running the uninstaller. But now I've lost 6gb of space from my first wubi installation and I've no idea where it has gone. Anyone help me on this?

---

### Post by dfk789 on 2009-01-10
Ok, sorted it out now. Found a folder called found.00. Inside that was a file called root.disk taking up 5.4gb and a swap of 600mb. Obviously my old install. Just deleted that and all my space was back. Awesome.:)

---

### Post by claracc on 2009-01-17
I have a similar problem but i couldn´t recover the 15 GB disk space occupied by ubuntu.
I installed ubuntu 8.10 as a vista application with Wubi, for one month everything was ok, one day ubuntu hanged and i had to turn off the computer with the button. Since then i couldn´t boot ubuntu because when i select ubuntu in the boot screen, appeared the grub prompt and said it couldn´t boot the kernel, so i boot the computer in vista mode, it made a chkdsk, apparently fix the disk, then i uninstalled ubuntu with wubi, all the folders with the name ubuntu disappeared but i haven´t recovered the 15 Gb that os ubuntu occupied. I see c: disk and everything is ok, there are not wubi or ubuntu folders nor strange partitions but i do not recover The 15 Gb of disk space. I have looking for folder as found.00, but i haven´t found any.Any solution please?. Is there any way from the console to find the missing Gb?.
Thank you very much in advance
Regards, Clara

---

### Post by claracc on 2009-01-17
Well, i have solved. I have found a folder named found.000 with a scanner disk software (TreeSize free) in the c directory. It is a hidden folder that you have to locate with some special disk occupation software, i have executed the console as administrator and i  have deleted all the files in this folder and then the folder. I have recovered the 15 Gb which were occupied by so ubuntu.
Regards, Clara

---

