---
title: "Update Manager Corrupted?"
date: 2007-07-26
forum: Dell  Ubuntu Support
---

### Post by Jaconius on 2007-07-26
Ok, i recently attempted to download a program called "VirtualBox" which is basically an OS emulator that works with .ISOs. So during download, my internet dropped and i had to restart my computer. When i got back, i deleted the package contents, and went on my way. The next day, i noticed a new update, so i clicked on the Update Manager and it says:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

And now i can't update.

Do i have to run something in the terminal?

I tried downloading and it didn't work.

---

### Post by lsutiger on 2007-07-26
try this 
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by Jaconius on 2007-07-27
Thank you so much, it worked perfectly.

---

