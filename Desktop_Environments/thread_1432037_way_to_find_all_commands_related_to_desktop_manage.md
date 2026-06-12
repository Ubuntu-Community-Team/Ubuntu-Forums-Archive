---
title: "way to find all commands related to desktop management?"
date: 2010-03-17
forum: Desktop Environments
---

### Post by silencej on 2010-03-17
There are times that the desktop environment is messed-up and all the icons disappear, with opened terminal windows kept. I want to log out with command in terminal, and search:
```
man -k log out
```just gave lots of commands and i tried some but none work. So i have to "sudo shutdown -r".

At last google helped me and i know gnome-session-save --kill could log one off.

The question is, is there a way for people finding what commands could be used to perform the same as the regular operations with GUI in the desktop environment?

P.S. The network management GUI of Karmic always fails to initiate the NIC for me. So i wrote a script ready to use anytime.

P.P.S. Any suggestions to improve the "man -k" search instead of "man -k log out" are also welcome. I have to agree the man -k can't compete google. But google demands us to be online, what if something unknown happens to your Ubuntu to stop you go online?

---

### Post by jtprince on 2010-03-17
This would be a great resource that I would use.  I don't think it really exists right now.

I logout on the command line with this:
```
gnome-session-save --logout
```

A lot of file commands can be performed the same as with a gui file manager (such as nautilus) with ```
gvfs-<some_command>.
```

More complicated commands use dbus-send.

Others?

---

### Post by aeiah on 2010-03-17
i usually just kill gdm if things bork like that. ill ctrl+alt+F1 to the shell then issue
```

sudo /etc/init.d/gdm restart

```

although that might not be preferable

---

### Post by silencej on 2010-03-19
Thanks guys. We now have more than one option when coming across gdm-brokedown.

---

