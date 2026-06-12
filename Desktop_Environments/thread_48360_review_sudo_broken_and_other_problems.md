---
title: "review: sudo broken and other problems"
date: 2005-07-12
forum: Desktop Environments
---

### Post by pilpi on 2005-07-12
[http://pilpi.net/journal/item-912.php](http://pilpi.net/journal/item-912.php)

Love Ubuntu. Period.  \\:D/ 

The lack of ready-made DVD, Flash and MP3 flattens my excitement though.

I wrote a review and questions for example about sudo not working at all - should I post the same text here, too, or just keep it in my blog?

Thanks  :-)

---

### Post by Juergen on 2005-07-12
> sudo not working at allIt seems you're confusing yourself if you insist on having the root account enabled.
By default you don't have a root-password and sudo asks for YOUR password.

Did you read [http://ubuntuguide.org](http://ubuntuguide.org) and [http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root) ?

> should I post the same text hereFor me a link is enough.

---

### Post by pilpi on 2005-07-12
Oh! Thank you for that.

 That's interesting ... anyway, I do remember trying most of the admin buttons/menu commands with my own password, too. No luck. Not sure if I tested sudo on the cmd line with my own password. Will have to get back on that next week.

Strange that I have a root account in the system then... I remember being asked for a root password in the installation, is this possible (expert mode)? Or did going to the .shadow file and emptying the password entry there "enable" the account?

---

### Post by pilpi on 2005-07-13
had time today anyway: 

```
a@pc040:~$ sudo ls
Password:
a is not in the sudoers file.  This incident will be reported.
a@pc040:~$
```


```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

```

---

### Post by angkor on 2005-07-13
Seems fair enough. 'a' is not listed in the sudoers file. Is 'a' the user you created at install? You need to add 'a' to the sudoers file. Just append a line beneath the root=all line:

a    ALL=(ALL) ALL

---

### Post by Juergen on 2005-07-13
> Or did going to the .shadow file and emptying the password entry there "enable" the account?To 'disabe' an account, the hash stored in the shadow-file is set to a string/character that is never the result of the hashing algorithm.
That way no password you could enter would match the stored hash.

If you clear the hash that would AFAIK just mean 'no password' and such enabling the account again. (Don't let root run around without password!! ;-))

> 'a' is not listed in the sudoers file.The first account you create is normally added to the sudoers by the setup.
Don't know what happened to you, just add yourself as mentioned.

---

### Post by pilpi on 2005-07-23
[QUOTE=][/QUOTE]
 I *did* set the root password after resetting it, yeah :).
Thanks, it all works now. Could this have happened because I used the expert setup?

---

### Post by kinnla on 2005-07-23
i had the same problem after install at experts mode:
- root account enabled and registered at the sudoer file,
- user account enabled but not registered at the sudoers file.
> a ALL=(ALL) ALL worked great for me, too. Thx, angkor, kamsahamnida!

by the way, after 5 days having ubuntu installed it makes a very good impression to me. and this forum is great -- all my problems appeared so far could be fixed with your help. really nice community!

---

