---
title: "How to remove unnecessary modules in bootup"
date: 2005-02-17
forum: Desktop Environments
---

### Post by nanaban on 2005-02-17
I don't think RAID and LVM are needed for my system, how to I stop them from starting ? I remember doing something like rc-update in gentoo....

Thanks.

---

### Post by cyberchills on 2005-02-17
Are you sure they are starting? Or are they modules being loaded.  If they are services actually being started you should check out "update-rc.d"  pretty good man on it.  If you don't like the CLI then emerge , i mean apt-get install rcconf.  

Now if it is module being loaded you should recompile your kernel for necessary hardware support.  Then do a mkinitrd to create the initrd for bootime.

apt-get install kernel-source ( this will get you a good list of avail sources)

---

### Post by illek on 2005-02-17
Just comment out(put an underscore at the beginning of the filename) the services in rc2.d that you don't want to start.  Don't delete them as they are Symlinks that you might need later.

---

### Post by nanaban on 2005-02-17
[QUOTE=illek]Just comment out(put an underscore at the beginning of the filename) the services in rc2.d that you don't want to start.  Don't delete them as they are Symlinks that you might need later.[/QUOTE]
Thanks a lot.

---

