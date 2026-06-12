---
title: "Some locale admin tasks ..."
date: 2006-08-02
forum: Desktop Environments
---

### Post by gab on 2006-08-02
I wonder if it is possible to give normal users more privileges, but not make them member of the admin group. Some things can be done by editing /etc/sudoers, but not all. I like the way print administration is enabled by being member of the lpadmin group.

The case is that I'm a SysAdm and has some users whit Ubuntu on there desktop, and I would allow them to do:

Upgrade, not installing. - sudoable
Adding printers – Fixed whit lpadmin group
Change screen resolution – not tested

But they shall not be member of the admin group. I've tested adding them to /etc/sudoers on there desktop so that they can do upgrade-manger, and upgrade-notifier. Upgrade-manager works whit sudo, but not upgrade-notifier!?!!?? To run upgrade-notifier you have to be member of the admin group. I do not understand the sense in this. I would say that EVERY user should be able to see that there are upgrades available!!!

Is there any other way around then make them member of the admin group? If not I would recommend this possibility for the next Ubuntu release.

---

