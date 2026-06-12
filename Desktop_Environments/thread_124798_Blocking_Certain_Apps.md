---
title: "Blocking Certain Apps"
date: 2006-02-02
forum: Desktop Environments
---

### Post by SpiKeRs on 2006-02-02
Whenever people use my computer they always end up dling rubbish, changing the themes, wallpaper etc etc. Ive created a seperate account for them but tbh I would rather lock down everything I dont want them to use, like they do on public networks and such, so that they can only run the basics like openoffice, gimp, gaim, and not be able to change wallpaper or themes, etc. Im not sure exactly how to do it, can anyone help?

---

### Post by el3ktro on 2006-02-02
You could try and set all the permissions for the programs you don't want them to run accordingly. Or you configure the system how you want it for these other users, make a copy of it and then write a little script that always copies this backup back to the user profile. When you run this script whenever the restricted user logs out, the original configuration is written back, and when the restricted user logs in again, all changes are gone. Just an idea though.

KDE has something called Kiosk mode which is exactly what you need, perhaps you can have a look at this.

Tom

---

