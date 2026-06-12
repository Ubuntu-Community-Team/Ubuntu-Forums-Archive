---
title: "detect outgoing connections/allow user to block them?"
date: 2009-03-22
forum: Desktop Environments
---

### Post by graysky on 2009-03-22
I'm looking for software that will detect when an application is opening up an outgoing connection, and prompt the user to allow/disallow it.  I've been googling around and found one for MacOSX that does this called [little snitch](http://www.obdev.at/products/littlesnitch/index.html) but it seems to be exclusively for MacOS.  Is there an equivalent for LINUX?

---

### Post by lovinglinux on 2009-03-23
First of all, this discussion would be better placed on [Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338") forum.

Anyways, I guess you will not find such an application for Linux. Blocking new connections attempts and generate alerts is a Windows thing. Most Linux programs will not phone home and if they do, there isn't much to be worried about, unless you download software from untrusted sources. If you stick with the repositories, then you should be fine.

You could use UFW firewall manager tho. It seems that it has application based filtering support now, so you can block connections per application, but I doubt it will alert you and give you the choice to allow or deny the connection from an application not configured in the firewall.

Another option would be to use Apparmor, which can restrict what each application on your system can do, including network access. This is much more than an connection filter, since it can prevent zero day attacks by not allowing applications to have access to certain areas of the system and to certain actions (like writing to user folders for example). Check the tutorial below:

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

