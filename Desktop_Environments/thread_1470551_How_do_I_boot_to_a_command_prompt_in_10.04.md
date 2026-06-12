---
title: "How do I boot to a command prompt in 10.04?"
date: 2010-05-02
forum: Desktop Environments
---

### Post by eddyjackson on 2010-05-02
Is it possible to prevent X from starting on boot and just give me a CLI?

---

### Post by akand074 on 2010-05-02
Umm Ctrl+Alt+F1 should bring you right into the command line on boot. Also you can try this:

```
sudo update-rc.d -f gdm remove
```

or edit the /etc/inittab file to boot into CLI instead of your desktop environment. Though I don't know very much on the topic.

---

### Post by eddyjackson on 2010-05-03
Thanks for the tips, but "sudo update-rc.d -f gdm remove" doesn't work in recent versions and I don't even have a /etc/inittab file.

The only thing I've been able to do is comment out the following line from the /etc/init/gdm.conf file:

```
exec gdm-binary $CONFIG_FILE
```

It still seems to start X, and display an ubuntu splash screen. I wish I could figure out how to stop it before that and just have it dump me to a console login.

---

### Post by akand074 on 2010-05-03
> **eddyjackson said:**
> Thanks for the tips, but "sudo update-rc.d -f gdm remove" doesn't work in recent versions and I don't even have a /etc/inittab file.

The only thing I've been able to do is comment out the following line from the /etc/init/gdm.conf file:

```
exec gdm-binary $CONFIG_FILE
```It still seems to start X, and display an ubuntu splash screen. I wish I could figure out how to stop it before that and just have it dump me to a console login.

oh what about this:

```
sudo gedit /etc/default/grub
```

and find this:

```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
```

change it to this

```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash text”
```

then

```
sudo update-grub
```

let me know how that works.

---

### Post by eddyjackson on 2010-05-09
Thank you! That worked smashingly.

---

