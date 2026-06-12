---
title: "USplash Editing."
date: 2008-12-23
forum: General Help
---

### Post by BoomAM on 2008-12-23
Hi.
Can anyone give me any help with Usplash editing?
I dont really like the boot up/shutdown splash screen that Ubuntu uses.
Im quite particular to the big list thing that Knoppix uses for boots and shutdowns. Is it possible to have Ubuntu do the same?

Thanks in advance all. :)

---

### Post by BoomAM on 2008-12-23
Hi.
Can anyone give me any help with Usplash editing?
I dont really like the boot up/shutdown splash screen that Ubuntu uses.
Im quite particular to the big list thing that Knoppix uses for boots and shutdowns. Is it possible to have Ubuntu do the same?

Thanks in advance all. :)

---

### Post by laero on 2008-12-23
There is a package named "startupmanager" that provides a graphical interface for editing the settings for GRUB and usplash. You can download it by typing:

```
sudo apt-get install startupmanager
```

---

### Post by edog76 on 2008-12-23
I lack the expertise to give you complete control, but I can give you a couple options.

You can manipulate the Usplash using startup manager (you'll need to install the application from the repositories). It will install in System>Admin>Startup-Manager. From there you can manage and change Usplash themes. Themes are available at [gnome-look.org](gnome-look.org). You can also manage and change the Grub menu from here as well.

Alternatively you could go the terminal route. Old tutorial: [http://ubuntuforums.org/showthread.php?t=185538](http://ubuntuforums.org/showthread.php?t=185538)
You probably don't want to use the splash theme there since it was for 6.04 but that should give you an idea.

---

### Post by BoomAM on 2008-12-23
> **edog76 said:**
> I lack the expertise to give you complete control, but I can give you a couple options.

You can manipulate the Usplash using startup manager (you'll need to install the application from the repositories). It will install in System>Admin>Startup-Manager. From there you can manage and change Usplash themes. Themes are available at [gnome-look.org](gnome-look.org). You can also manage and change the Grub menu from here as well.

Alternatively you could go the terminal route. Old tutorial: [http://ubuntuforums.org/showthread.php?t=185538](http://ubuntuforums.org/showthread.php?t=185538)
You probably don't want to use the splash theme there since it was for 6.04 but that should give you an idea.
I cant see any 'themes' around on there that look like what i want. They all literally just look like new pictures with a loading screen.
The expanded Fedora loader looks nice, if i can find one like that...

---

