---
title: "Updates as Sudo"
date: 2005-09-16
forum: Desktop Environments
---

### Post by N8MAN1068 on 2005-09-16
Is there a way to set the updates to run as Sudo automatically?
I was going to put Ubuntu on an old machine for the bosses daughter, however, this is going to be an issue.

The only way I see around this, is to enable Root, disable the standard user account, then have Root automatically sign on at boot. [-X 

Is there a way to add a user to the Root group so that they aren't prompted to enter a password for updates?

---

### Post by bsussman on 2005-09-16
Yes but it is not considered a very good idea. When anybody does anything in the sysadm world on the machine, requiring them to switch modes to the more powerful mode is prudent.  Especially when what they are about to do can make the machine unuseable (apt is wonderful but not perfect)

Than being said, if you look at the doc for the sudoers file, it documents the NOPASSWORD option. 

the manpage is pretty good:

 ```
> man sudoers
``` 

also probably there is more friendly doc online somewhere in the universe O:)

I do not know how to do this from a gooey screen, since I don't do it.  There probably is a way.

---

