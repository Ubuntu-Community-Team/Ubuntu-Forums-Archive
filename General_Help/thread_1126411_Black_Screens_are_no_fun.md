---
title: "Black Screens are no fun"
date: 2009-04-15
forum: General Help
---

### Post by bundyxc on 2009-04-15
So today I go to load up my Edubuntu box, and it won't let me login. After the loading screen, there should be a login, but it's just a black screen..

I've been having problems with my machine (as it's making everything in the monitor yellow), but that's about it. I haven't installed anything (hardware/software), and haven't changed a thing.

I shut down my computer fine last time, and then just tried to load it up a few days later.. and it didn't work.

Black screeeeeeen.
Can anybody help?

Thanks guys.

---

### Post by Tipped OuT on 2009-04-15
Maybe a little bit more info like what hardware you're using? Also, it might just be a bad installation.

---

### Post by bundyxc on 2009-04-15
Installation is fine.. as it's been up and running just fine as my LAMPP server for over a year. I'm a hardware noob, so what do you want me to tell you?

---

### Post by jbrown96 on 2009-04-15
What kind of graphics card do you have? If Nvidia or ATI, do you use the proprietary drivers?


It's most likely a problem that a new kernel is being used, and the drivers did not update correctly. When the computer boots, press ESc to get to the grub menu, then try choosing an older kernel. If you can boot, go to the hardware drivers (System--->Admin) and disable the graphics driver. Reboot normally using the default kernel. Re-enable the drivers and reboot again.

---

