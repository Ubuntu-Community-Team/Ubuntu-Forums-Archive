---
title: "No Desktop - Drop into shell at boot"
date: 2010-10-23
forum: Desktop Environments
---

### Post by reef2dive on 2010-10-23
I have a laptop IBM R50e. A clean install using 10.04.1 has been done, and all updates have been loaded.
At boot, the system does not start the desktop. It tries and drops into the shell. I have started the recovery boot, and tried failsafeX start, but it only returns into the shell.
The boot parameter i915.modeset=1 has been set. There are a number of issues with the Intel graphics card and 10.04, I have been through those without success.
The modeset makes it possible to start some graphical environmrnt using xinit or startx. startx starts gnome, but lot of functionality is missing, like the network applet. Additionally I notice that there is no file /var/run/dbus/system_bus_socket, which my other laptop has when in gnome.

Started gdm when being in the graphical shell through xinit, gives the error message that /var/run/dbus/system_bus_socket is missing.

Any ideas where to look to fix this.

---

### Post by cornflake000 on 2010-11-04
I have exactly the same problem w/ a dell inspiron 700m.  I have nothing to add except I am trying to figure this out as well.

---

### Post by reef2dive on 2010-11-07
I am getting a little further. When I set --verbose on the bootup grub2, I can see the dbus is started and then fails. I do not know why yet as the message only states that and no reasons.
Looking at the gdm start in init, it requires dbus running to be able to start.
(I do not have the exact file names in front of me, I can provide them later.)

---

### Post by Bucky Ball on 2010-11-07
You could try logging in (to the shell) and as long as you have a hardwire connection (or any internet connection) try:

```
 sudo apt-get install gnome-panel
```

or

```
 sudo apt-get install ubuntu-desktop
```

Might get you a bit closer.

---

### Post by reef2dive on 2010-12-03
Got it :)
The fresh installation of 10.04 does create the file machine_id, but it is empty.
```

/var/lib/dbus/machine-id

```
This has as a result that dbus does not start, which stops gdm from starting at boot-up. Using startx may work, but e.g. audio does not work.
I created the file by using the following sequence in the terminal
```

sudo dbus-uuidgen > machine-id
mv machine-id /var/lib/dbus/machine-id

```
With this setup, gdm came up using the rescue mode.
To be able to boot into gdm the setup according to [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) needs to be applied:
```

echo options i915 modeset=1 | sudo tee /etc/modeprobe.d/i915-kms.conf
sudo update-initramfs -u

```
After a reboot, gdm started normally.

---

