---
title: "Problems with gdmsetup"
date: 2006-10-05
forum: Desktop Environments
---

### Post by Aurelius on 2006-10-05
I recently started having a problem with GDM setup. I don't know exactly when it started happening.

If I go to System/Administration/Login Window, I get nothing. If I run gdmsetup from the terminal, I get the following

```

david@desktop:~$ sudo gdmsetup
Could not access GDM configuration file.

```

gdm.conf exists:
```

david@desktop:/$ locate gdm.conf
/var/lib/dpkg/info/gdm.conffiles
/var/lib/dpkg/info/gdm.config
/etc/gdm/factory-gdm.conf
/etc/gdm/gdm.conf
/etc/gdm/gdm.conf-custom.xgl
/etc/xdg/xubuntu/gdm/gdm.conf

```

I've tried manually specifying the config file to run, but it still tells me it could not access the file
```

david@desktop:/$ sudo gdmsetup --config=/etc/gdm/gdm.conf-custom
Could not access GDM configuration file.

```

The permissions on gdm.conf and gdm.conf-custom seem fine.
```

david@desktop:/etc/X11/gdm$ ls -l gdm.conf
-rw-r--r-- 1 root root 27912 2006-08-02 09:04 gdm.conf
david@desktop:/etc/X11/gdm$ ls -l gdm.conf-custom
-rw-r--r-- 1 root root 1839 2006-09-06 22:35 gdm.conf-custom

```

GDM works fine - I just can't configure it. Anyone got any suggestions?

---

### Post by Aurelius on 2006-10-06
Bump - anyone got any ideas?

---

