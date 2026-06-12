---
title: "Disable GNOME from boot!"
date: 2010-01-07
forum: Desktop Environments
---

### Post by Deathspike on 2010-01-07
Hello,

I've been trying to remove Ubuntu from the boot process. A lot of different resources show a lot of different solutions, none which worked for me. I've started out with a base server (9.10) and added a [minimal GNOME installation](http://community.spiceworks.com/how_to/show/156). Now I want to prevent GNOME from starting unless I specify to do so (startx)!

Using sysv-rc-conf I've disabled GDM for any run level. Then I have installed BUM to remove GNOME there as well. However, it's still starting and I can't seem to figure out why. Please help me out, what can be starting GNOME?!

Thanks for any help you may provide,
Deathspike

---

### Post by Deathspike on 2010-01-08
Anyone?

---

### Post by m0o on 2010-01-08
Try using update-rc.d:

```
sudo update-rc.d -f gdm remove
```

---

### Post by Leppie on 2010-01-09
i would edit the upstart gdm.conf file:
```
gksudo gedit /etc/init/gdm.conf
```
edit the "start on" section to something like this:
```
start on (runlevel [345]
	  and filesystem
	  and started hal
	  and tty-device-added KERNEL=tty7
	  and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0126]
```
this should boot runlevel 2 (default runlevel) in cli, also changing to runlevel 2 will automatically kill your x session.

---

### Post by falconindy on 2010-01-09
Add 'text' to your kernel options in GRUB.

---

### Post by efflandt on 2010-01-09
Wouldn't **single** in the kernel boot options boot to single user mode in a console (like the recovery menu entries)?  Change any options in /etc/default/grub (not /boot/grub/grub.cfg which gets rewritten after any update-grub).

---

### Post by falconindy on 2010-01-10
> **efflandt said:**
> Wouldn't **single** in the kernel boot options boot to single user mode in a console (like the recovery menu entries)?  Change any options in /etc/default/grub (not /boot/grub/grub.cfg which gets rewritten after any update-grub).

Booting to single user mode means that you're forced into root access via recovery mode. You'd be forced to bring the system up to a multi user level manually, as continuing the boot process would start GDM...

The 'text' option simply boots normally but prevents your login manager from starting.

---

### Post by Deathspike on 2010-01-11
All these suggestions work great on 8.04, but not on 9.10.
This new start up manager is fishy >.<

---

### Post by Leppie on 2010-01-11
> **Deathspike said:**
> All these suggestions work great on 8.04, but not on 9.10.
This new start up manager is fishy >.<
i am using the modified gdm.conf with karmic and it's working great. setting up runlevels provides the possibility to easily change system setup.
change runlevels using telinit, for example:
```
sudo telinit 3
```

---

### Post by barnex on 2010-01-11
alternative:

edit the file:
```
/etc/X11/default-display-manager
```
replace the line: ```
/usr/bin/gdm
``` by: ```
/bin/false
```

cheers

---

### Post by foxmajik on 2010-05-23
> **barnex said:**
> alternative:

edit the file:
```
/etc/X11/default-display-manager
```
replace the line: ```
/usr/bin/gdm
``` by: ```
/bin/false
```

cheers

I tried this, but I found that after the system is done booting the boot splash with the animated dots stays on the screen indefinitely.

---

