---
title: "resolution in x settings gets removed on boot"
date: 2010-06-22
forum: Desktop Environments
---

### Post by ihavenoidea on 2010-06-22
Every time i boot up my computer (ubuntu 10.04) my screen resolution gets reset back to 800x600 when i want 1024x800. I save the configuration file, and when my computer starts i get this line in xorg.conf, 

"# Removed Option "metamodes" "1024x768 +0+0; nvidia-auto-select +0+0""

What program is causing this?

---

### Post by Frogs Hair on 2010-06-22
In my case 1024 x 800 is not a valid resolution for my monitor so it defaults to the native resolution . I also use Nvidia x server settings because of my driver choice.

---

### Post by ihavenoidea on 2010-06-22
except that is the resolution my monitor supports, and i do use the nvidia control panel.....

---

