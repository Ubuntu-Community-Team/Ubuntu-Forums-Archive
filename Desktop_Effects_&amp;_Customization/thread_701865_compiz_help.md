---
title: "compiz help"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by bvav22 on 2008-02-19
ok well yesterday, i got my radeon drivers working, then installed compiz and enable the effects, twas amazing, had the works, the cube wobbly windows all that working. well today i come home and turn my laptop on, loging, and the screen is only visible in the top left corner..... i dont think its my resolution becuase it still maintains the same size, just you can only see that corner. i am able to turn off the visual effects by right clicking the desktop and it goes back to my normal screen......



anyone seen this or have any clue how i can get my effects back?

---

### Post by bvav22 on 2008-02-19
ok well i did this, i set my resolution to 640x480, and enabled visual effects, and it worked! so i know think that somewhere my monitor is configured incorrectly cuasing compiz to try and display in 640x480...


well should i try to look in xorg.conf, or does xgl have any play in this?


also i noticed my ati control panel no longer works... it reads the following error:

"Failed to execute child process "amdcccle" (No such file or directory)

---

### Post by northern lights on 2008-02-19
If you can open ccsm, then check "General Options", select the "Display Settings" tab - what is listed under "Outputs"?
And is the "Detect Outputs" box checkmarked?

---

### Post by bvav22 on 2008-02-19
bah long story short, im on a fresh install of gutsy agian :(

anyways i have the drivers working and composite extension set to "1" yet i still cannot enable the effects. i think i remember install xgl but i dont remember if that was it

---

