---
title: "gimp printing problems"
date: 2005-04-10
forum: Desktop Environments
---

### Post by trenths on 2005-04-10
I recently installed the Pixus driver for my Canon I560 and it works great in every application but GIMP.  When I go to print in GIMP the printer's power light starts to blink and the printer makes a few warm up noises but nothing ever prints. I loaded some other Canon drivers which are supposed to work with this printer model but still no go. GIMP just doesn't want to print. Any ideas?

---

### Post by trenths on 2005-04-11
I think I figured out some things. First of all, GIMP uses its own printer drivers (you can view the make and model options under the "Setup Printer" choice in GIMP's Print interface). If your main printer driver choice is not found in GIMP's printer options, you won't be able to print in GIMP. Secondly,  for GIMP assings a "Post Script 2" level to the printer by default. If you leave it there, it won't print. You have to change that by actually choose you printer make and model from the drop down box and the save the settings or it will revert back to Post Script 2 on the next load.

---

### Post by tomp88 on 2005-05-10
[QUOTE=][/QUOTE]
 I use Turboprint for my Canon i560 in Gimp, and I've had the identical problem.  Turboprint mentions this in their help files and says to open Gimp from a terminal window by typing:
    
     export LC_NUMERIC =C
     gimp 2.2                          (substitute your gimp version)

after doing that all is well.
Good luck.

tomp88

---

### Post by neighborlee on 2005-05-12
[QUOTE=tomp88]I use Turboprint for my Canon i560 in Gimp, and I've had the identical problem.  Turboprint mentions this in their help files and says to open Gimp from a terminal window by typing:
    
     export LC_NUMERIC =C
     gimp 2.2                          (substitute your gimp version)

after doing that all is well.
Good luck.

tomp88[/QUOTE]
---------
what is this supposed to do ??

my printer is a HP officejet 5500 and im' having same problems because my printer isn't showin in drop downlist either...I can't try this right now but I will when I get back into linux

thx
neighborlee

---

