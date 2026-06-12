---
title: "wine segmentation fault-- help?"
date: 2006-01-19
forum: General Help
---

### Post by bulldogzerofive on 2006-01-19
Hey all

I've been trying to install a multimedia dictionary for windows in wine.  So far I have been pretty successful in tracing wine's error messages to the fault that I have to fix when installing stuff, until this one.  So, here is the verbose mode:

1.  The dictionary is called the petit larousse 2005.  It is unbelievably well copy protected using a utility calling itself PROTECT.dll.  This provents me from installing it in virtual machines under qemu or vmware-- it will not verify the CD properly.  It requires flash media player and has to be run in NT 4.0 emulation because wine cannot support dxv-- when i run it under windows XP it is one of those typically problematic (and insecure) Windows programs that has to run with admin access to work, not as a user.

2.  The wine version is 0.9.5.  I used winetoolkit version 2.0 to install things like "base system", windows installer, fonts, IE, etc.

3.  The flash version is 7 from macromedia, obviously.

4.  The original install of "PL_2005.exe", as the dictionary program is called, had the usual wine errors: missing .dlls, this failed, that went wrong, etc.  These were all easy to track down because of the wonderfully useful error output that wine provides.  After a bit of tweaking everything seems to have installed properly.

5.  Now for the tricky part:  I run the program.  The first thing that pops up is CD verification.  I enter the CD key, no problem, the window dissappears, and nothing.  After a minute wine exits with the error message: "segmentation fault."

6.  I try to run the program with winedbg, but then the dictionary gives me a dialogue box informing me that it cannot be run with debugging utilities and exits.

I tried to google this one, but "segmentation fault" appears to have so many possible meanings and solutions that I am frankly at a loss.  I am pretty sure that there are detailed HOWTOs for this dictionary and wine out there, but they are all in french and my french is not that good.

So, if anybody has any idea how to proceed I would be deeply greatful.

Thanks,

mh

---

