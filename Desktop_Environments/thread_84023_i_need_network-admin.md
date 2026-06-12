---
title: "i need network-admin"
date: 2005-10-30
forum: Desktop Environments
---

### Post by ^NoX on 2005-10-30
I am using ubuntu for more than a year now. Currently Breezy.
Everytime there is a new distro out, I replace my sources.list and dist-upgrade.
I saw that my little brother (which uses Breezy too, but installed from the Breezy CD) has a program called network-admin, and I don't have it.
I have searched APT, and I don't find it.

What to do? I need that program in order to config my ethernet.

Thank you very much,
Ofer Shaked.

---

### Post by ^NoX on 2005-10-30
please, somebody?

---

### Post by Zwack on 2005-10-30
gnome-system-tools provides network-admin...  If that's installed you should have it.

Can you become root and run network-admin manually?

Z.

---

### Post by ^NoX on 2005-10-30
[QUOTE=Zwack]gnome-system-tools provides network-admin...  If that's installed you should have it.

Can you become root and run network-admin manually?

Z.[/QUOTE]

Thank you very very much! It worked.

---

### Post by bluetoad on 2005-10-30
[QUOTE=Zwack]gnome-system-tools provides network-admin...  If that's installed you should have it.

Can you become root and run network-admin manually?

Z.[/QUOTE]

To fix it so you can access it from System/Administration/Networking menu.

You'll need to be in the adm group.  Probably the easiest way is to type

user-admin (as root)
click on your user 
click on properties
click on user privileges
Give yourself access to 'Executing system administration tasks'

                                                                               ...Peter




                                                                       ...Peter

---

