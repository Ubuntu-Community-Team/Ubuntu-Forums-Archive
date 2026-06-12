---
title: "jaunty, black screen after new install and a few tweaks"
date: 2009-04-30
forum: Desktop Environments
---

### Post by sparklyprgs on 2009-04-30
Just installed 9.04, pulled down updates, and all was testing out fine. So installed Wine and VirtualBox with a few basic tweaks - nothing advanced! (auto log in etc)

Upon reboot (both normal and recovery), it just gets to a black screen with mouse pointer, no hard drive activity. i can get to the cltr-alt consoles login and look at the system, but don't know what to really look for. And i can ping it, but the Gnome seems stuck!

A strange thing..... if i login via a console, then do "sudo shutdown now", the recovery menu comes up! So I used to to fsck, xfix and dpkg but it didn't change anything.

Before I rebuild it (which is fine to do, it's just a test), any hints on what sort of commands to use to check logs \ settings in case I can report a potential bug? I wrote down everything I did so I can try to reproduce it.  Thanks!

---

### Post by sparklyprgs on 2009-05-01
The problem was VirtualBox! I reloaded 9.04 and installed VB 2.1.4_OSE from the package manager and it was fine.  But using 2.2.2 from this link:

[http://download.virtualbox.org/virtualbox/2.2.2/virtualbox-2.2_2.2.2-46594_Ubuntu_jaunty_i386.deb](http://download.virtualbox.org/virtualbox/2.2.2/virtualbox-2.2_2.2.2-46594_Ubuntu_jaunty_i386.deb)

makes Ubuntu not boot to a proper desktop.

---

