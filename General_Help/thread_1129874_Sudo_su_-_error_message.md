---
title: "Sudo su - error message"
date: 2009-04-19
forum: General Help
---

### Post by Asparagustime on 2009-04-19
When i try to do sudo [command] to execute as root I get the below message after putting in my password:

sh: /usr/share/samba/panic-action: not found
Segmentation fault

Also, I logged on this morning and found that I was unable to do anything because the file-system had become read-only overnight. I found that this may mean there is a file system problem.

Several commands such as ls and nano don't work anymore.

Thanks in advance!

---

### Post by Peter09 on 2009-04-19
Have you tried going in with recovery mode?

---

### Post by Asparagustime on 2009-04-19
It's a remote machine so I've not been able to.

I realise that trying to fix the problem remotely might be impossible but I thought I'd ask anyway.

---

### Post by sumit.kalra999 on 2009-04-19
reboot the system, its sometimes become hard to handle.

or wait for next day to boot your system or try to repair the system using live cd.

---

### Post by Josef_A on 2009-04-19
I'd take the system's networking down first. Bonus points if you can aptitude install chkrootkit first.

Then I might have a look at what mount reports and compare that against mount options in /etc/fstab

Then - depending on your partitioning scheme - I'd unmount such volumes as I could (obviously not including whichever partition /sbin is on) and fsck them.

And while you're at it, set aside some time to go out to wherever the server is with repair disks and some form of rootkit checker on live cd.

If it's a long drive or flight, print out the system logs and read them on the way.

---

