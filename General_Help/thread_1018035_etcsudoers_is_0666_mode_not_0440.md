---
title: "etc/sudoers is 0666 mode not 0440"
date: 2008-12-21
forum: General Help
---

### Post by psenkodej on 2008-12-21
Hello,
Everytime I try to sudo, I get /etc/sudoers is mode 0666, should be 0440. Than I rebooted in recovery mode and went to Drop to root shell prompt and ask from me to give root password for maintenance. But I'm not allowed to type anything.

Please for a little help, thanks

---

### Post by oldos2er on 2008-12-21
It's normal not to see anything echoed to the screen when you enter your password; go ahead and type it in, and press 'Enter.'

---

### Post by jerome1232 on 2008-12-21
Sounds like you followed a tut to enable root for some reason in Ubuntu, normally this isn't needed and can cause breakage. You can type your root password in, it's normal for it to not echo back any characters, this is for security purposes (so people looking over your shoulder can't see how long your password is type of thing)

Just boot back into recovery mode enter your root password then 
```
chmod 0440 /etc/sudoers
reboot
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

There's a section in there that will tell you how to re-lock the root account if you so wish to do so.

---

### Post by psenkodej on 2008-12-21
I typed root password but get answer login incorect. What now?

---

### Post by jerome1232 on 2008-12-21
> **psenkodej said:**
> I typed root password but get answer login incorect. What now?

If you can't remember the password at all then you can boot a live cd, mount your root partition under /mnt then chmod it from the live cd.

Assuming your root partition is /dev/sda1 this will do it from the live cd.

```
sudo -i
mount /dev/sda1 /mnt
chmod 0440 /mnt/etc/sudoers
reboot
```

---

### Post by sisco311 on 2008-12-21
You can use a live cd to restore the file permission.



Or in the grub menu highlight the Ubuntu menu entry (NOT the recovery mode)

hit e for edit, then highlight the kernel line and hit e again

remove *ro quiet splash* from the end of the line and

append it with *init=/bin/bash* and hit Enter then b to boot.

in the shell type:
```
chmod 0440 /etc/sudoers
```

```
reboot
```or press Ctrl+Alt+Del

---

### Post by psenkodej on 2008-12-21
Well, I past login and typed what you said but when I reboot system and try to work and I get a new message that /etc/sudoers is owned by uid1000, should be 0...

---

### Post by sisco311 on 2008-12-21
d'oh!

in the root shell type:
```
chown root:root /etc/sudoers
```

[Read this]("https://help.ubuntu.com/community/Sudoers") before you try to edit the sudoers file again.

---

### Post by psenkodej on 2008-12-21
Thanks man, it works!!

---

### Post by sisco311 on 2008-12-21
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

Marking threads as [SOLVED], after a solution has been found will help
others to find an expedient solution for their own issues.

---

