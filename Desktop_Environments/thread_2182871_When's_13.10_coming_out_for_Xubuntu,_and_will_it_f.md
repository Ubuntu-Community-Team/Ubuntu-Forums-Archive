---
title: "When's 13.10 coming out for Xubuntu, and will it fix my installation?"
date: 2013-10-22
forum: Desktop Environments
---

### Post by jimford on 2013-10-22
I'm sick of the problems I've been having after 'upgrading'(!) from 12.10 to 13.04. Every time I log on I get another frustrating problem!

When 13.10 comes out, is it likely to overwrite a corrupted configuration and fix my problems, or will they remain and I'll have to flatten and rebuild, please?

I'm really getting to the end of my tether!

Jim

---

### Post by Frogs Hair on 2013-10-22
[http://xubuntu.org/news/tag/13-10/](http://xubuntu.org/news/tag/13-10/)

---

### Post by hansdown on 2013-10-22
Hi jimford.

For the first time ever, I did an upgrade last night.

Went flawlessly, and works great.

---

### Post by jimford on 2013-10-23
Nope - 'sudo apt-get dist-upgrade' does nothing except return "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded." (I checked that I am in fact running 13.04 in /etc/os-release.)

I also get a pop-up inviting me to upgrade to 13.10, but selecting the upgrade box does nothing.

Yet another feature that's broken on my system. I'm discovering new ones every day!

Looks like a flatten and rebuild is looming ever closer, but I'm not looking forward to it!

Thanks for the replies.

Jim

---

### Post by grahammechanical on 2013-10-23
You misunderstand what dist-upgrade means. Many people likewise misunderstand.

apt-get dist-upgrade does not upgrade to the next release. It upgrades the existing OS using methods more intelligent than apt-get upgrade.

That pop up should do something. Do you get error messages? They can be helpful. If not to you, then to anyone trying to help you.

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

Regards.

---

### Post by jimford on 2013-10-23
If I run the Update Manager, I get the invitation to update to 13.10. If I then open a terminal and do 'tail -f /var/log/syslog' and accept the pop-up invitation I get:

AptDaemon.Worker: INFO: Updating cache
AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/b0abb183e8e24a95a120b0977d5194bc

Then nothing more!

Thanks for the reply

Jim

---

