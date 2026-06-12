---
title: "Wine can't start offline rekening overzicht"
date: 2007-04-12
forum: Desktop Environments
---

### Post by Fíona on 2007-04-12
I have installed wine and want to run windows banking programs on ubuntu.
I downloaded one of the programs, offline rekening overzicht (a dutch program to download and browse my bank data on my computer), a zip file, unzipped it it became a .msi file and I installed it. I Installed direct to c:\Offline Rekening Overzicht and not in the default Program Files.

When I click on the executable in nautilus I get the following;
Cannot open /home/fiona/.wine/drive_c/Of...e Rekening Overzicht/orov.exe: No application suitable for automatic installation is available for handling this kind of file.


Now I get the following message when I type wine orov.exe on the command line;
wine: could not load L"c:\\windows\\system32\\orov.exe": Module not found

Anyone any ideas?

Thanks

---

### Post by justleen on 2007-04-12
i familiar with the tool, and tried to get it running. 
I managed to get to the initial screens after copying some dll's of my windows install.  It comes to the point creating the db, and after that crashes.


There is a fix for it how ever, but its a wine patch, so that would mean i had to recompile wine (after which i might get another error :) ) 

If your still interrested after this (im not sure how much efforts you wanna put in this ;) )to get in running, let me know.

---

### Post by Erik. on 2008-05-26
I also want to run the same program, is there someone who could help me whit this problem?

---

### Post by D.Stomp on 2008-06-07
copy the *.msi to .wine/c_drive/

then in terminal_window 

$ wine .wine/c_drive/xxxx.msi

wine installs the msi and a menu entry in wine gives you OROV!

---

### Post by peterhorlings on 2008-06-14
I followed your instructions, but I get the following error messages:

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
wine: could not load L"C:\\orov102.msi": Bad EXE format for 
[email]peter@peter-laptop:~/.wine[/email]/drive_c$ preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

Any suggestions, please.

---

