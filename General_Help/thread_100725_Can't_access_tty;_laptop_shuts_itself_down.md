---
title: "Can't access tty; laptop shuts itself down"
date: 2005-12-08
forum: General Help
---

### Post by Minilek on 2005-12-08
Hello.  I have been having problems ever since using Breezy with my laptop shutting itself off at random times (happens even when acpi is off).  This morning when it shut itself down, I turned it back on but then got the following error while booting up:

/bin/sh: can't access tty; job control turned off.

Booting then stops there and gives me some kind of very basic shell with diagnostic commands.

So, now I can't boot into Ubuntu.  Anyone have any ideas what may have happened?

---

### Post by Minilek on 2005-12-08
I should mention -- I also get a message beforehand saying /sbin/init was not found and that /dev/hdc4 (i think 4 at least...whichever is my linux partition) could not be mounted.

---

### Post by Bachstelze on 2005-12-08
try login in the shell and then running gdm.

---

### Post by Minilek on 2005-12-08
I can't run login because I don't have a "real" shell.  I get "Busybox v.1.00 - pre10 built-in shell (ash)".

When I boot, I get the following errors:

Mount: Mounting /dev/hdc4 on /root failed: Invalid argument
...
Target Filesystem doesn't have /sbin/init
Busybox v1.00-pre10 built-in shell(ash)

Then I get this shell with very limited ability.  I have no access to my hard-drive, so I can't login or run any programs (including gdm).

---

### Post by Minilek on 2005-12-09
Anyone have any ideas about how to go about solving this problem?  Unfortunately I am very new to Ubuntu (and linux in general), so I'm not even sure what I should be trying to do to fix this.

---

### Post by cocox on 2006-05-15
maybe this can help you

[http://ubuntuforums.org/showthread.php?t=174537&highlight=hdc+upgrade+breezy](http://ubuntuforums.org/showthread.php?t=174537&highlight=hdc+upgrade+breezy)

---

