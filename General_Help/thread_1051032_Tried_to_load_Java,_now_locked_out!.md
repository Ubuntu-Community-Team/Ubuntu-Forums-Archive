---
title: "Tried to load Java, now locked out!"
date: 2009-01-26
forum: General Help
---

### Post by Velcro on 2009-01-26
Java seemed to load ok, but couldn't figure out how indicate
"ok" on license agreement. Rebooted and now get I/O errors.
wtf's up with that??

---

### Post by taurus on 2009-01-26
Use the Tab key to highlight the <OK>.

---

### Post by Velcro on 2009-01-26
Thanks, but I can't get back in.

---

### Post by taurus on 2009-01-26
Can you post the complete error message?  If you can't type the whole thing, take a picture of the screen.

---

### Post by Velcro on 2009-01-26
Sure.
I'm running on a usb stick, if it makes any difference.

                *********************

*Starting GNOME Display Manager ...
/etc/init.d/usplash:  112:  clear:  Input/output error

*Starting deferred execution scheduler atd
/sbin/start-stop-daemon:  Unable to start /usr/sbin/atd:  Input/output error  (Input/output error)
/etc/rc2.d/s89cron:  49:  tail:  Input/output error 
/etc/rc2.d/s89cron:   1:  tail:  Input/output error  
/etc/rc2.d/s89cron:   1:  tail:  Input/output error  

*Starting periodic command scheduler crond
start-stop-daemon:  Unable to Start  /usr/sbin/cron:  Input/output error  (Input/output error) 

* Enabling additional executable binary formats binfmt-support
Missing right curly or square bracket at /usr/lib/perl/5.10/errno. pm line 139, at end of line
Syntax error at /usr/lib/perl/5.10/Errno.pm line 139, at EOF
Compilation failed in require at /usr/share/perl5/Binfmt/Format.pm line 24.
BEGIN failed-- compilation aborted at /usr/share/pelr5/Binfmt/Format.pm line 24
Compilation failed in require at /usr/sbin/update-binfmts line 25
BEGIN failed--compilation aborted at /usr/share/update-binfmts line 25

/etc/rc2.d/S98usplash: 112: clear:  Input/output error
/etc/rc2.d/S99 acpi-support: line 7:  /usr/share/acpi-support/power-funcs:  Input/output error

---

