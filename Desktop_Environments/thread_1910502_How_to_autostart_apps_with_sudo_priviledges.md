---
title: "How to autostart apps with sudo priviledges"
date: 2012-01-17
forum: Desktop Environments
---

### Post by maulynvia on 2012-01-17
When I auto start Jupiter (power saving on eeepc) it doesnt work properly - key settings made in the menu have no effect.

It does work properly if I run "sudo jupiter-run"

Is there a way to autostart apps with sudo priviledges?

---

### Post by fuduntu on 2012-01-17
> **maulynvia said:**
> When I auto start Jupiter (power saving on eeepc) it doesnt work properly - key settings made in the menu have no effect.

It does work properly if I run "sudo jupiter-run"

Is there a way to autostart apps with sudo priviledges?

Fix /etc/sudoers, or move the Jupiter sudoers group to /etc/sudoers.d.  Jupiter should be the very last rule in the chain.

---

### Post by maulynvia on 2012-01-17
Thanks, any tips on how to do this?

I looked at [http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html) which looks quite scary!:confused:

---

### Post by fuduntu on 2012-01-17
> **maulynvia said:**
> Thanks, any tips on how to do this?

I looked at [http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html) which looks quite scary!:confused:
Move the %jupiter line to the bottom of the file.

---

### Post by mister_p_1998 on 2012-01-17
Whats wrong with Sudo crontab -e
@reboot /usr/bin/jupiter

????

---

### Post by SeijiSensei on 2012-01-17
Or putting the command in /etc/rc.local?

---

### Post by maulynvia on 2012-01-17
Editing sudoers and rebooting had no effect. Here is my sudoers file:


```
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d
%jupiter ALL=(ALL:ALL) ALL
```

:(

---

### Post by sudodus on 2012-01-17
> **maulynvia said:**
> Editing sudoers and rebooting had no effect. Here is my sudoers file:


```
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d
%jupiter ALL=(ALL:ALL) ALL
```:(
I am not sure but I think that you should remove the # sign from the beginning of the second last line:
```
includedir /etc/sudoers.d
``` Otherwise it is only a comment line.

---

### Post by fuduntu on 2012-01-17
> **maulynvia said:**
> Editing sudoers and rebooting had no effect. Here is my sudoers file:


```
%jupiter ALL=(ALL:ALL) ALL
```:(

Where did you get this configuration?  The Jupiter group should not be configured like that.

```
%jupiter ALL=NOPASSWD: /usr/lib/jupiter/scripts/bluetooth, /usr/lib/jupiter/scripts/cpu-control, /usr/lib/jupiter/scripts/resolutions, /usr/lib/jupiter/scripts/rotate, /usr/lib/jupiter/scripts/touchpad, /usr/lib/jupiter/scripts/vga-out, /usr/lib/jupiter/scripts/wifi
```

---

### Post by maulynvia on 2012-01-17
That fixed it, thanks funduntu. Jupiter is fantastic.

(There was no existing config for jupiter - how am I supposed to know this? I just copied the config for sudu):D

---

### Post by fuduntu on 2012-01-17
> **maulynvia said:**
> That fixed it, thanks funduntu. Jupiter is fantastic.

(There was no existing config for jupiter - how am I supposed to know this? I just copied the config for sudu):D

It should have been configured when the package is installed, weird.

---

