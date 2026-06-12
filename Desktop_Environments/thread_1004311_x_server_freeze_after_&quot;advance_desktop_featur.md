---
title: "x server freeze after &quot;advance desktop feature&quot; enabled"
date: 2008-12-07
forum: Desktop Environments
---

### Post by Ant68 on 2008-12-07
After a fresh 8.10 install, I have set up Nvidia driver, managed to boot and log in. I then enable the "advanced desktop features" from the desktop. When rebooting I cannot start the x server and I get a black screen after the ubuntu logo loads with the orange back in the middle.

I have tried to reboot in recovery mode with no much success. It seems that the X server start in recovery mode but the system freeze rapidly (i.e. a few seconds).

hemona@hemona-desktop:~$ lspci
...
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GT (rev a2)
...

I do not know what to do.
Maybe remove the advance desktop features using a command line.

do you have any suggestions?

---

