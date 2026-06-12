---
title: "File Permissions"
date: 2010-01-11
forum: Desktop Environments
---

### Post by sweeny_here on 2010-01-11
Recently I attempted to change file permissions on file etc/sudoers. However I used the wrong command and reset the usergroup to UID 730 from the default root UID 0. I would now like to change this back to default but when I run command


```

sudo chown root:root /etc/sudoers

```

it returns the following error

```

sudo: /etc/sudoers is owned by uid 730, should be 0

```

Here is the output from ls -ltn 

```

-r--r----- 1 730 0 557 2009-06-17 18:18 /etc/sudoers

```

Any ideas?

---

### Post by MooPi on 2010-01-11
You may want to move your thread to another category, as this is designated Desktop Environments. Sorry no clue on fie assoc.

---

### Post by SlugSlug on 2010-01-11
> **sweeny_here said:**
> Recently I attempted to change file permissions on file etc/sudoers. However I used the wrong command and reset the usergroup to UID 730 from the default root UID 0. I would now like to change this back to default but when I run command


```

sudo chown root:root /etc/sudoers

```it returns the following error

```

sudo: /etc/sudoers is owned by uid 730, should be 0

```Here is the output from ls -ltn 

```

-r--r----- 1 730 0 557 2009-06-17 18:18 /etc/sudoers

```Any ideas?



try reboot and use grub to drop to a root shell,

then try chown root:root again.

should look like 
-r--r----- 1 root root 581 2010-01-09 09:33 /etc/sudoers

---

### Post by prshah on 2010-01-11
> **sweeny_here said:**
> 
```

sudo chown root:root /etc/sudoers
sudo: /etc/sudoers is owned by uid 730, should be 0

```


You can use either recovery mode (from GRUB startup menu) or a live CD.

If you can boot into recovery mode, you will get a maintenance menu. Choose "Root Terminal" (or similar) option. Then at the command line give the command```
chown root:root /etc/sudoers
``` (Note no need to use sudo). Then reboot with the command```
reboot
```.

If that doesn't work, boot with a live CD. Open the terminal (Applications-Accessories-Terminal) and give the following commands```
sudo mount /dev/sdX9 /mnt -o defaults,rw
sudo chown root:root /etc/sudoers
sudo umount /mnt
sudo reboot
```

(Replace /dev/sdX9 with the actual partition that contains the "/etc" file system)

Please post back here if you want more help on this matter.

---

### Post by sweeny_here on 2010-01-11
The workaround was to

Restart and in Grub 
Select Recovery Mode
Drop to root shell
Run commands
```
chown root:root /etc/sudoers
reboot
```

Thank you very much for all the help :)

---

