---
title: "Starting lightdm Just Hangs"
date: 2014-09-18
forum: Desktop Environments
---

### Post by kenmoremathguy on 2014-09-18
I am on Server 14.04.1 with ubuntu-desktop installed.

I modified /etc/defaults/grub to launch in text-only.

I want to be able to run "sudo lightdm" when I occasionally need access to GNOME.

When I run "sudo lightdm", the screen goes blank for one second. After that, the screen returns to the command line. The lightdm executable has not finished; I need to press Ctrl-C to enter the next command in the shell.

I checked --debug and the logs. Nothing useful. Automatic login should be disabled.

---

### Post by deadflowr on 2014-09-18
```
sudo **start** lightdm
```

---

### Post by Bucky Ball on 2014-09-18
Or even:

sudo service start lightdm

I usually use:

sudo startlightdm

Works for me. ;)

---

