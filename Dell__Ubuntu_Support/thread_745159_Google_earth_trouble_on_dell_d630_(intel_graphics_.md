---
title: "Google earth trouble on dell d630 (intel graphics card)"
date: 2008-04-04
forum: Dell  Ubuntu Support
---

### Post by msvalente24 on 2008-04-04
Good day, i'm having trouble running google earth on my dell d630. When ever i launch gearth, the system restarts. My pc has an intel graphics card, 2gb ram, ubuntu 7.10 if that helps. Any help, i would greatly appreciatte?

Thanks

---

### Post by logos34 on 2008-04-04
How much system memory is allocated for frame buffer (-->Bios)?  Google recommends at least 32MB.  Maybe that's an issue.

---

### Post by msvalente24 on 2008-04-05
Um i wouldnt know and wouldnt how to check, i'm slightly new to linux. however i found that if i launch google earth with the following command

DISPLAY=:0 googleearth

it runs fine and stable but without a window border containg the min, max and close buttons, resizing the window is therefore not possible. could it possibly be compiz, becuase on my system when i enable full visual effects there are serious bugs also.

---

### Post by msvalente24 on 2008-04-07
it seems like the same thing happens for blender in winowed mode, wings 3d and equinox 3d

---

### Post by msvalente24 on 2008-04-07
could it prossibly be a problem with the window manager

---

