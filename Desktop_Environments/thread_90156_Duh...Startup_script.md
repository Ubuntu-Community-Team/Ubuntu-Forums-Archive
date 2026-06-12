---
title: "Duh...Startup script?"
date: 2005-11-14
forum: Desktop Environments
---

### Post by quietglow on 2005-11-14
I know I should know this but...

If I have a script in, say, /etc/init.d that I want to run automagically at startup, how would I do that? Like if I want a module, I put it in /etc/modules...if I want a script I put its path...where?

Thanks!

---

### Post by floppy on 2005-11-14
It depends, to some extent, on just when you want it to run. Here's a bit of an explanation from the documentation for BUM (boot-up manager) that explains some of this. Hope it helps:
[http://www.marzocca.net/linux/bumdocs.html#order](http://www.marzocca.net/linux/bumdocs.html#order)

---

### Post by Ufo on 2005-11-14
You could use "update-rc.d" command to create links in  /etc/rcrunlevel.d/ directory. Look info update-rc.d
Another way is to use Boot-up manager (bum package in universe repository) if you prefer graphical interfaces.
And of course you could manually make links in  /etc/rcrunlevel.d/ directories.

---

### Post by quietglow on 2005-11-14
The update-rc.d is what I needed. I'd just throw it in via BUM, but I'm trying to write a HowTo for our school's crappy Cisco VPN client. The install script doesn't quite work on it and the VPN module doesn't get auto-loaded at boot (like its supposed to). I need to break it down to a command that people can key in as part of the install so an update-rc.d works perfectly. Thanks!

---

