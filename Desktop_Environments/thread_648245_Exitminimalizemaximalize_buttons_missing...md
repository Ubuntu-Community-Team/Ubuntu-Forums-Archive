---
title: "Exit/minimalize/maximalize buttons missing.."
date: 2007-12-23
forum: Desktop Environments
---

### Post by -Shy Guy- on 2007-12-23
Hi all,

I have a weird problem, I've been using ubuntu for a while now and everything worked.. But when i logged in today some things were changed. The exit/minimalize/maximalize buttons are missing and i only have 2 workspaces instead of the usual 4. I have extra visual effects  installed. I tried metaspace --replace, it works but the visual effects become basic. When i try to put it back on extra the buttons go missing again.. I need some help.

Thanks in advance

---

### Post by ubutufan on 2007-12-23
What graphics card are you using? nVidia or ATI?

---

### Post by -Shy Guy- on 2007-12-23
Ati

---

### Post by ubutufan on 2007-12-23
Try the following steps in case fglrx is broken (for any reason)
Disable 3d effects
In synaptics locate xorg-driver-fglrx and reinstall
Reboot
Enable 3d effects


Let us know


Sorry. Did you check if the restricted drivers is enabled?

---

### Post by -Shy Guy- on 2007-12-23
The resricted drivers are enabled. Ok, i tried what you said but it didn't work.. :( The same trouble strung up again. Got any other idea's?

Thanks in Advance.

---

