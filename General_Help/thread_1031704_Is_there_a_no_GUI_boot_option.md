---
title: "Is there a no GUI boot option?"
date: 2009-01-05
forum: General Help
---

### Post by emarkay on 2009-01-05
After logging in, instead of the progress bar, can the boot process be shown as text, like the Windows "NoGUI boot" option?

Thanks!

---

### Post by rjmoerland on 2009-01-05
In grub, when about to boot, press escape to enter the grub menu. Then, select the kernel you want to boot (usually first entry). Press 'E' to edit the line. Now select the line that starts with 'kernel' and press 'E' again. Go to the end of the line and remove 'quiet' for text info while booting and remove 'splash' as well for no graphics at all. 

**The following can damage your installation!**
To make this permanent, you will need to edit your /boot/grub/menu.lst. You will need to be root (use sudo). Find the line '# defoptions=quiet splash' and remove what you like. Save, close and run 
```

sudo update-grub

```

to make the edits permanent.

---

### Post by Titan8990 on 2009-01-05
Yes, you just need to remove "quiet splash" from your boot line in /boot/grub/menu.lst.

First thing, make a backup of menu.lst:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.BAK

then edit the file:

sudo nano /boot/grub/menu.lst


Look for the kernel line ( kernel= ), and delete "quiet splash" from the end.

hit CTRL+X to exit and save when prompted to.


```
sudo update-grub
```

This generates a menu.lst. Why would the OP need to run that after manually editing the file???

---

### Post by rjmoerland on 2009-01-05
> **Titan8990 said:**
> Look for the kernel line ( kernel= ), and delete "quiet splash" from the end.

I would advise against directly editing the kernel=... lines, as this will interfere with the update-grub script. This script is run when a new kernel is installed as an update. update-grub will make sure that whatever extra options you had, or didn't have, will be applied as well to the newly installed kernel. That way you don't need to edit the kernel= line again after a new kernel is installed and you won't have the update-manager complaining to you that you manually edited the file :)

---

### Post by Titan8990 on 2009-01-05
Maybe I have just been compiling my own kernels and writing my own menu.lst/grub.conf files for too long. I would always trust my manual edit over some "automagic" script, especially if I only need to delete **two** words.

---

