---
title: "login without need to type &quot;startx&quot;"
date: 2009-11-07
forum: Desktop Environments
---

### Post by akhe on 2009-11-07
please can someone tell me how (if) is possible to boot to console instead of graphical login, to just write username and password and it will automatically startx (without need to type "startx") ??? thank you!

---

### Post by falconindy on 2009-11-07
If you append "text" to the kernel line in your grub config, you'll get a text based login. Create  $HOME/.xinitrc with a single line "exec gnome-session". Edit your .bashrc to add a line to the end: "[[ `pgrep Xorg` ]] || startx".

However, there is one problem with this solution: you cannot logout back to the prompt. Ubuntu blindly expects GDM to be running and just leaves you with a blank desktop waiting for the non-existant GDM to take over. Perhaps a bug?

---

### Post by akhe on 2009-11-07
*However, there is one problem with this solution: you cannot logout back to the prompt. Ubuntu blindly expects GDM to be running and just leaves you with a blank desktop waiting for the non-existant GDM to take over. Perhaps a bug?*

before I will try to do this config, I must ask this question: what exactly is that problem???
It will make no possibility to logout, or shutdown? or? sorry, I dont understand english so much... thanks

---

### Post by falconindy on 2009-11-08
You cannot log out from GNOME back to the console. But, I'm not sure why you would do this because (if you could) as soon you log in at the console, you'll be back in GNOME. 

If you're the only user on this computer and you ignore the 'log out' button in Gnome, this solution works.

I'm interested to see if anything becomes of my [bug report]("https://bugs.launchpad.net/bugs/478019") regarding this.

---

