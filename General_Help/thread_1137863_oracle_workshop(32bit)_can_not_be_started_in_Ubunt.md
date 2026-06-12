---
title: "oracle workshop(32bit) can not be started in Ubuntu 9.04(64bit)"
date: 2009-04-26
forum: General Help
---

### Post by garriot on 2009-04-26
Hi all,
I want to use oracle service bus with oracle workshop in Ubuntu 9.04 (64 bit).
I can not start oracle workshop after the installation.
When I run the workshop command in terminal, it is blocked at the splash window. And in the output, there are some errors:
```

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

```

Maybe the reason is that the OS is 64 bit but the application is 32 bit. 
I already installed ia32-libs. But the problem is not resolved.

Do you guys have any ideas about this issue?

Thanks in advance

---

### Post by dwschulze on 2009-06-06
Did you ever get this resloved?  

I want to run OSB / Workshop on 9.04 desktop 64 bit, but after reading this I'm wondering if I need to go with a distro. that Oracle officially supports for OSB.

Thanks.

Dean

---

