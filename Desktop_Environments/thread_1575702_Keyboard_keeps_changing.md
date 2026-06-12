---
title: "Keyboard keeps changing"
date: 2010-09-16
forum: Desktop Environments
---

### Post by Findarato on 2010-09-16
Hello,

During my ubuntu installation, I specified a UK keyboard. Since, I have changed this to a swiss one and I have added the swiss keyboard layout to my settings. However, even though I delete my UK layout, everytime I reboot my computer, it is back again (AND it's set as the default). How would I possibly change my default keyboard layout to a swiss keyboard forever? 

Thanks,

Josh

---

### Post by sikander3786 on 2010-09-16
I think you need to execute the following command after selecting your default layout and applying it system wide. See the links for details.

```

sudo dpkg-reconfigure console-setup

```

[http://ubuntuforums.org/showthread.php?t=1371238](http://ubuntuforums.org/showthread.php?t=1371238)

[http://ubuntuforums.org/showthread.php?t=281616](http://ubuntuforums.org/showthread.php?t=281616)

---

