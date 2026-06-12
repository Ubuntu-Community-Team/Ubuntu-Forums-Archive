---
title: "Third mouse button emulation"
date: 2005-05-04
forum: Gaming &amp; Leisure
---

### Post by Takis on 2005-05-04
I'm running Jedi Academy with WINE, and one of the button combos you (might) commonly press is left-click + right-click - which under TMB emulation translates as the middle button instead. Does anyone know how you change this setting? TIA

---

### Post by Juergen on 2005-05-04
You have to edit your /etc/X11/xorg.conf.

Put a '#' before 'Option "Emulate3Buttons"' to comment it out and then restart X11 (log out and then press <CTRL>+<ALT>+<BACKSPACE>)

---

### Post by Takis on 2005-05-04
Out of curiousity, why is this enabled at all? Extra functionality for older (2 button) mice?

---

### Post by amunimanghi on 2006-04-26
i had this problem and found the solution.  you have to click mouse one  **_THEN_** mouse 2. (left click then right click) and it will work for the saber and the melee.   can you fly any ships?

---

