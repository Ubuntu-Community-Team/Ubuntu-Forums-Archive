---
title: "Mouse pointer changes from desktop to programs..."
date: 2010-03-10
forum: Desktop Environments
---

### Post by diaz028 on 2010-03-10
My mouse pointer goes from regular white pointer when on the desktop / app bar, to the black oxygen theme cursor when on a web browser or nautilus when hovering over the |-|+|x| boxes...

Thanks!

-D

---

### Post by perky on 2010-04-20
Hello

I'm getting the same problem.

It's the same as [this]("http://ubuntuforums.org/showthread.php?t=583635") one, but I cannot find 'the field "Cursor Theme" under the General tab in General Options' in compizconfig-settings-manager.

Did you have any luck fixing it?

---

### Post by UberStudent on 2010-05-23
You might try resetting your system default cursor.

To do that run ```
sudo update-alternatives --config x-cursor-theme
``` and select the number for the cursor you wish, and then logout and back in.

~

---

