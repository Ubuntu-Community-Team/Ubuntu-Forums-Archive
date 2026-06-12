---
title: "Disable GUI on Ubuntu 19.04"
date: 2019-06-30
forum: Desktop Environments
---

### Post by g00d-fabio-r00t on 2019-06-30
[FONT=arial]Hi All
What is the way to (only disable GUI) a t boot on ubuntu 19.04?

I have tried modify grub:[/FONT]
```
sudo vi /etc/default/grub
```    
```
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
``` comment it and 

add

```
 GRUB_CMDLINE_LINUX_DEFAULT="text"
```


  ```
sudo update-grub


```

[FONT=arial]In union with: [/FONT]```

 systemctl enable multi-user.target
```

[FONT=arial]But the system returns:[/FONT]

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

[FONT=arial]After reboot nothing is changed (gui start regulary)

Thanks
[/FONT]

---

### Post by sisco311 on 2019-06-30
I think you have to do:
```
sudo systemctl set-default multi-user.target
```

---

### Post by g00d-fabio-r00t on 2019-06-30
Thanks sisco311, i'confirm:

```
 systemctl set-default multi-user.target
```

it's ok without any other modify

For rollback reason this is for come back in GUI mode

```
 systemctl set-default graphical.target
```

---

### Post by hk42 on 2019-09-03
Thanks for the nice tip.
When in text mode you can start the GUI with startx.
BUT avoid sudo startx .
If you do that some files in your home directory are changed to owner root.
And you can no more log as a normal user

---

