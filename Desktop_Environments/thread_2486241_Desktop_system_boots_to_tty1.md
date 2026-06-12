---
title: "Desktop system boots to tty1"
date: 2023-04-24
forum: Desktop Environments
---

### Post by marklft on 2023-04-24
Whenever I reboot my Ubuntu Desktop system, instead of booting the the graphical login, it boots to the tty1 console login.

If I then login, and use sudo systemctl start gdm3.service, I am presented with my usual graphical front end.

I tried using sudo systemctl enable gdm3.service, but this fails.

I have tried to use sudo apt install --reinstall gdm3, this seems to work, but I still boot into the tty1 prompt.

Is there a command that I can use to reset all the graphical config and binary files to a standard desktop?   Or maybe someone else has experienced this, and can point me in the right direct to fix it.

I really don't want to have to rebuild this system as it has a lot of development software installed plus secret keys, repositories etc. It would be a nightmare trying to build it again from scratch.

---

### Post by ActionParsnip on 2023-04-24
What is the output of:
```

sudo systemctl enable gdm3.service

```
We can then see the failure. Simply saying "it fails" doesn't really tell us much

---

### Post by marklft on 2023-04-24
```
sudo systemctl enable gdm3.service

```

```

Synchronizing state of gdm3.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable gdm3
The unit files have no installation config (WantedBy=, RequiredBy=, Also=,
Alias= settings in the [Install] section, and DefaultInstance= for template
units). This means they are not meant to be enabled using systemctl.


Possible reasons for having this kind of units are:
• A unit may be statically enabled by being symlinked from another unit's
  .wants/ or .requires/ directory.
• A unit's purpose may be to act as a helper for some other unit which has
  a requirement dependency on it.
• A unit may be started when needed via activation (socket, path, timer,
  D-Bus, udev, scripted systemctl call, ...).
• In case of template units, the unit is meant to be enabled with some
  instance name specified.

```

---

### Post by idmbe on 2023-04-24
Try this
```
sudo apt-get install --reinstall gdm3 gnome-shell
```

Then
```
sudo dpkg-reconfigure gdm3
```

---

### Post by marklft on 2023-04-24
I have tried this previously, but have just tried again. When these commands are entered the prompts indicate all worked correctly, but upon reboot, it still boots to tty1 console.  In addition trying to enable the gdm3 service gives exactly the same message as before.

---

### Post by idmbe on 2023-04-24
So type
```
sudo systemctl set-default graphical.target
```

Then reboot ,if you want to go back then
```
sudo systemctl set-default multi-user.target
```

If all else fails 
```
sudo apt-get install ubuntu-desktop
```

---

### Post by marklft on 2023-04-24
First one no change.

install desktop states it is already installed, so does nothing.  So I have also tried with --reinstall flag, seems to reinstall desktop, but still boots back into the tty1 console.

Thanks for the suggestions though.

---

### Post by idmbe on 2023-04-25
First try this
```
systemctl enable fprintd.service
```

then
```
systemctl start fprintd.service
```


If not work follow this:
[https://wiki.debian.org/GDM](https://wiki.debian.org/GDM)

---

### Post by marklft on 2023-04-25
The enable and start of fprintd.service produces basically the same result as trying to enable the gdm3 service.

Will follow the other link now.

---

### Post by marklft on 2023-04-25
Thanks for the link, I have been through every stage, but alas, no change.  Still booting to tty1.

---

### Post by idmbe on 2023-04-25
That strange, ok try this
```
 ln -sf /lib/systemd/system/gdm.service /etc/systemd/system/display-manager.service
```

if not work try to do it again and reinstall gdm again then see.

if not work after that try this:
```
systemctl disable display-manager
```

---

### Post by marklft on 2023-04-25
The first command fixed it.  I now reboot into the GUI as I expected.

Many thanks.

---

