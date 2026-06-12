---
title: "Resolution Problems"
date: 2005-11-01
forum: Desktop Environments
---

### Post by kapa_des on 2005-11-01
How can I change to 1024x768 with out changeing the file xorg.conf, with the terminal but only the resolution not the hole configuration ... PLZ Help

---

### Post by kapa_des on 2005-11-01
plz someone answer me ....

---

### Post by l33tc0d34 on 2005-11-01
i have problems 2 with black screen. can u help?

---

### Post by kapa_des on 2005-11-01
no ... i can't help ... i can't eaven soulf my own problems  ... so plz someone answer me

---

### Post by l33tc0d34 on 2005-11-01
i just ask. you don't have 2 be mean :-(
whats ur problem then?

---

### Post by kapa_des on 2005-11-01
How can I change to 1024x768 with out changeing the file xorg.conf, with the terminal but only the resolution not the hole configuration ...

---

### Post by l33tc0d34 on 2005-11-01
i don't understand what ur asking? do u know how to fix a black screen on linex?

---

### Post by angkor on 2005-11-01
[QUOTE=kapa_des]How can I change to 1024x768 with out changeing the file xorg.conf, with the terminal but only the resolution not the hole configuration ...[/QUOTE]

I assume you have tried going to System -> Preferences -> Screen Resolution.

If that doesn't work you need to run:

sudo dpkg-reconfigure xserver-xorg

in the terminal (sorry) ;) and make sure you enter the correct horizontal sync and vertical refresh rates for your monitor (read your monitor's manual or google the specs for your type of monitor.) 

You should then be able to change to the desired resolution if your monitor supports it.

Try the search button on the forum, it is explained in many threads.

---

