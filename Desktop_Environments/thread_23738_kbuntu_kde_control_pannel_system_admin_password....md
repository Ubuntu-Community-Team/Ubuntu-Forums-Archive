---
title: "kbuntu kde control pannel system admin password..."
date: 2005-04-03
forum: Desktop Environments
---

### Post by kristi on 2005-04-03
I did searches on this.   One said try your user password.  But that just gives me the kde control panel screen,  Another person said "ubunto" , but that just  said  "invalid password".

In KDEcontrol panel I am trying to change users.  I click on administration, it asks for password.  What do I do.
tia
Kristi

---

### Post by bored2k on 2005-04-03
[QUOTE=kristi]I did searches on this.one said try your user password.  just gives me the kde control panel screen,  Another said "ubunto"  said invalid password.

In control panel I am trying to change users.  I click on administration, it asks for password.  What do I do.
tia
Kristi[/QUOTE]
 From a terminal run sudo kcontrol .

---

### Post by kristi on 2005-04-03
Thanks - worked just fine.
Kristi

---

### Post by fizgig on 2005-04-03
I modified my start menu to make the command to start the control center be:
[b]kdesu kcontrol -caption "%c" %i %m

[/b]I get asked for my password when I start the control panel but I then can switch to any screen and not have to enter my password again.

---

### Post by kristi on 2005-04-04
Thanks for the tip.

I found that I have to check run as a different user, and put "root" as the user before it will bless me with asking for my password.   kdesu or sudo would do it.

nice idea!!!!!
Kristi

---

