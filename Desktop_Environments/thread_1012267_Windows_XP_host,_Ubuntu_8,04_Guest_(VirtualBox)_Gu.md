---
title: "Windows XP host, Ubuntu 8,04 Guest (VirtualBox) Guest Additions not working."
date: 2008-12-15
forum: Desktop Environments
---

### Post by moltendorf on 2008-12-15
***Edit:** Skip to paragraph 3 if you don't want the life story.*

I wasn't sure where to post this. But I have been using Ubuntu for a little over 8 months now with no problems, got my development environment set up running PHP 6 from snaps.php.net, and MySQL 6 and whatnot (on Ubuntu **not** running in VirtualBox).

After being kicked off my computer for the night (parents), I went downstairs to my laptop, and decided to give VirtualBox a whirl, installed Ubuntu on it with no problems, and Guest Additions with no problem, and noticed the one thing that would make life so much easier for a PHP developer like myself who likes to develop in a Linux environment (since it's so much more flexible in how you can customize PHP, and whatnot) but game in Windows (my computer is too slow to play games emulated in Wine).

Well, now that I'm on my normal system again, I decided to fire up VirtualBox, and figured out how to use an existing partition to run as a guest OS (so I wouldn't have to copy all my code, and preferences, and PHP installations). Everything worked, it's a little slow, though (probably since my computer is like 1/10 the power of that laptop). Everything worked **except** the Guest Additions installation, which installed fine, showed "OK" in the logs when starting up with the OS, but nothing changed... No mouse integration, no neat Seamless Mode, no changing of resolutions dynamically. Nothing.

Quickfacts for the confused (Okay, maybe not that, but rather, a little more specific, non-story-structured information):
[list][*]Ubuntu is booting up successfully and I can log in under VirtualBox.
[*]The Guest Additions were installed successfully on Ubuntu on both computers.
[*]The Guest Additions both loaded properly on both virtualized instances of Ubuntu.
[*]The Guest Additions did not provide any extra functionality in the one I loaded from the real partition on my second hard drive.
[*]The one with the functioning Guest Additions is running Ubuntu 8.10.
[*]The one with the **non** functioning Guest Additions is running Ubuntu 8.04.[/list]

P.S. Sorry for the life story. :P

---

