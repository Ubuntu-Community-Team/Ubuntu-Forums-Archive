---
title: "A simple preference editor for grub, please"
date: 2010-07-06
forum: Desktop Environments
---

### Post by julianbury on 2010-07-06
**\etc\grub.d** is an abomination! 
Nobody should have to read and edit that incomprehensible code.

Will somebody please write an application to set a users' preferences in grub, 
that allows naive users to set the timeout at the top of a list, 
followed by boot menu entries in order of preference like this:

timeout_seconds: 40
UBUNTU_10.04
Windows_XP_Pro
memory_test_mode
repair_mode
end

I wish I could do it myself but I am one of the naive and cannot grok the mess of code.

Have mercy on your newcomers, I beg of you.

Thank you for your kind attention (-_-)

---

### Post by scott1541 on 2010-07-06
If you by preferences you mean editing the grub boot list then that is easy, providing you are using Grub 2   

just run ```
 sudo gedit /etc/default/grub 
```

then you need to edit this section
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

Grub default is the default os, 0 being at the top of the boot list and ascending until the last one (eg first= 0 second= 1 third= 3)

Grub timeout is the menu timeout in seconds

When you have edited the file save it, close it then run..
```
sudo update-grub 
```

Sorted...

---

