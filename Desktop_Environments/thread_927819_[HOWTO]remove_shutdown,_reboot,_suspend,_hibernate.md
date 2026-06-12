---
title: "[HOWTO]remove shutdown, reboot, suspend, hibernate from logout menu"
date: 2008-09-23
forum: Desktop Environments
---

### Post by hayalci on 2008-09-23
in the following thread, someone asks how to remove hibernate and suspend from logout menu for all users, as that thread is archived I post this howto here.
[http://ubuntuforums.org/showthread.php?t=229665]("http://ubuntuforums.org/showthread.php?t=229665")

In our case, we want people to be able to shutdown/reboot machines from login screen(gdm greeter) but we don't want any power related items in logout menu to prevent accidential shutdowns.

To remove reboot and halt, the following suffices in a default gdm.conf file
```
sudo sed -i 's/^AllowLogoutActions=HALT;REBOOT;HIBERNATE;SUSPEND;CUSTOM_CMD$/AllowLogoutActions=CUSTOM_CMD/' /etc/gdm/gdm.conf
```

If you want to remove the power options from the greeter as well, use this;
```
sudo sed -i 's/^SystemCommandsInMenu=HALT;REBOOT;HIBERNATE;SUSPEND;CUSTOM_CMD$/SystemCommandsInMenu=CUSTOM_CMD/' /etc/gdm/gdm.conf
```

To remove hibernate and suspend for all users, put the following in "/etc/gconf/gconf.xml.mandatory/%gconf-tree.xml". 
```

<?xml version="1.0"?>
<gconf>
        <dir name="apps">
                <dir name="gnome-power-manager">
                        <dir name="general">
                                <entry name="can_hibernate" mtime="1222181472" type="bool" value="false">
                                </entry>
                                <entry name="can_suspend" mtime="1222181436" type="bool" value="false">
                                </entry>
                        </dir>
                </dir>
        </dir>
</gconf>

```
This file is empty by default, if not you can edit the xml by hand 
OR follow the steps
[LIST]
[*]run gconf-editor as root ("sudo gconf-editor")
[*]from File menu select "new mandatory window"
[*]click at the root ("/")
[*]right click at the empty place to the right, with name-value columns, then click "new key"
[*]type "app/gnome-power-manager/general/can_hibernate" in path, select "boolean" as type, make sure value os set to "false"
[*]repeat the same for  "app/gnome-power-manager/general/can_suspend"
[*]close the windows, there is no "save" button.
[/LIST]

:guitar:

---

### Post by edlutz on 2008-10-31
Thanks for the tips.

I just upgraded to Ubuntu 8.10 and tried the steps above but they didn't seem to work, even after restarting gdm, forcing gdm to reload configuration, killing X or whatever. There are still entries for shut down, hibernate, etc., on the logout menu.

Other ideas?

---

### Post by hayalci on 2009-03-05
The gconf daemon must be running on the background. You could have killed the gconfd process, or restarted the machine.

---

### Post by dwhitney67 on 2009-04-30
> **hayalci said:**
> ...
To remove hibernate and suspend for all users, put the following in "/etc/gconf/gconf.xml.mandatory/%gconf-tree.xml". 
```

<?xml version="1.0"?>
<gconf>
        <dir name="apps">
                <dir name="gnome-power-manager">
                        <dir name="general">
                                <entry name="can_hibernate" mtime="1222181472" type="bool" value="false">
                                </entry>
                                <entry name="can_suspend" mtime="1222181436" type="bool" value="false">
                                </entry>
                        </dir>
                </dir>
        </dir>
</gconf>

```
...

Is this solution applicable only to Ubuntu, or will it work with other Linux distros running Gnome?  I ask because it does not work with CentOS.

I am interested in removing (for all users) the **System->Suspend** menu option.

---

### Post by cccc on 2011-05-02
> **dwhitney67 said:**
> Is this solution applicable only to Ubuntu, or will it work with other Linux distros running Gnome?  I ask because it does not work with CentOS.

I am interested in removing (for all users) the **System->Suspend** menu option.

It doesn't work on Debian Squeeze.

---

