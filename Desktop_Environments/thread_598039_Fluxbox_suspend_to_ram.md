---
title: "Fluxbox suspend to ram"
date: 2007-10-31
forum: Desktop Environments
---

### Post by luke2760 on 2007-10-31
So I've got Fluxbox running nicely, almost everything I need out of a window manager. The last thing I need to to is get it to quit prompting me for a password when I hit my suspend hotkey.

So, I have a key bound to sudo /etc/acpi/sleep.sh. I've added these lines to my sudoers file:

%admin ALL=NOPASSWD: /etc/acpi/sleep.sh
%username ALL=NOPASSWD: /etc/acpi/sleep.sh
username ALL= NOPASSWD: /etc/acpi/sleep.sh

When I added the first line, everything worked fine, hit my hotkey, computer suspended. Resumed, everything looked peachy keen. Now, whenever I go to suspend, it doesn't work, so I replace sudo /etc... with gksudo /etc/acpi/sleep.sh. I also do it from the terminal, and both cases, it's prompting me for a password. What gives?

When I run sleep.sh from a command line, this is what the terminal looks like on resume:
```

$ sudo /etc/acpi/sleep.sh 
[sudo] password for username:
ifdown: interface eth0 not configured
 * Shutting down ALSA...                                                 [ OK ] 
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
Function not supported
Ignoring unknown interface eth0=eth0.
 * Setting up ALSA...                                                    [ OK ] 
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
$

```

---

