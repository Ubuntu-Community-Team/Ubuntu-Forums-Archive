---
title: "Rename a User?"
date: 2005-01-20
forum: Desktop Environments
---

### Post by ZakZak on 2005-01-20
How do I rename a user on Ubuntu?  Is it simply a matter of editing /etc/sudoers, /etc/passwd, and /etc/shadow to change the name?  Or is there a "right" way to do it?

-Zak

---

### Post by shmonkey on 2005-01-21
You can do it with the usermod command.

man usermod for more info

Not sure  sure if it can be done through Gnome tools or not.

---

### Post by matid on 2005-01-21
That's how you do it using Gnome Tools

Open Desktop->Administration->Users and Groups
Then choose an user and click 'Properties'. There you have (Account->Basic Settings) a field called 'Username'. Change it and click OK. Then close 'User and groups' window by clicking OK in order to save the changes.

---

