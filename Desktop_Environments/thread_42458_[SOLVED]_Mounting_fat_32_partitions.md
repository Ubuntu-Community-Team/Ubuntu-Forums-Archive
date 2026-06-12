---
title: "[SOLVED] Mounting fat 32 partitions"
date: 2005-06-17
forum: Desktop Environments
---

### Post by manicka on 2005-06-17
When I installed 5.04 I used expert partitioning to set up rw access to my shared fat 32 drive. An fstab entry was created that looked like this.

```
/dev/hdb5       /vidnphotos vfat    defaults 0 0
```

This was fine and there were no error messages when booting. In nautilus it looked like the partion is writeable but I couldnt make any changes to it at all.

To solve this I changed the fstab entry to
```
/dev/hdb5       /vidnphotos vfat    rw,users,gid=users,umask=000, 0 0
```

This worked and gave me rw access, but I now have the partition mounted on my desktop, which I don't want.

Can anyone suggest a better fstab entry so that I have rw access to this partiton and it won't appear on the desktop?

---

### Post by tread on 2005-06-17
You can just disable it from being visible on the desktop.

Go to Applications->System->Configuration Editor, and somewhere under apps, nautilus you should find check boxes which can set what is visible on the desktop.

---

### Post by manicka on 2005-06-17
[QUOTE=tread]You can just disable it from being visible on the desktop.

Go to Applications->System->Configuration Editor, and somewhere under apps, nautilus you should find check boxes which can set what is visible on the desktop.[/QUOTE]
Great    :grin:  thanks

I'm new to gnome/ubuntu after being a dedicated SuSE/KDE man for a number of years. 

Really enjoying gnome, as I find all the extra tweaks and configs and what control panel does what. It also helps using a distro that really does Gnome well.

thanks again  \\:D/

---

### Post by manicka on 2005-06-17
that's wierd.

Rebooting rather than remounting didn't mount the partition on the desktop. Oh well, thanks for the tip anyway. Always good to learn something new :)

Edit: Reboot and they're back again  :?

---

