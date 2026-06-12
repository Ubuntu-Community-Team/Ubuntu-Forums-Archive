---
title: "Logout applet: remove 'Switch User' button"
date: 2008-04-27
forum: Desktop Environments
---

### Post by x1a4 on 2008-04-27
Hi,

Is there a way to remove the 'Switch User' button from the logout applet?  I'm familiar with 

~/.config/xfce4-session/xfce4-session.rc

but nothing I added to its [General] section worked, the way it does with Hibernate and Suspend buttons. 

Thank you.

EDIT: I'm using Xubuntu Hardy

---

### Post by Skip Da Shu on 2008-05-02
Watching for Xubuntu response would also like to do this to wife's Ubuntu machine.

---

### Post by x1a4 on 2008-05-13
*bump* :(

---

### Post by x1a4 on 2008-06-14
Anyone?

---

### Post by Skip Da Shu on 2008-06-15
> **Skip Da Shu said:**
> Watching for Xubuntu response would also like to do this to wife's Ubuntu machine.

Converted her machine to Xubuntu... but still need this.

---

### Post by x1a4 on 2008-08-09
[color=green]bump[/color]er cars

---

### Post by crjackson on 2008-09-20
I'm looking for the same thing in Ubuntu 8.04 so I'll bump this up too...

---

### Post by crjackson on 2008-09-20
okay I figured this out for Ubuntu...

Terminal>gconf-editor

desktop>gnome>lockdown>disable_user_switching and tick the check box

DONE!

---

### Post by x1a4 on 2008-09-22
> **crjackson said:**
> desktop>gnome>lockdown>disable_user_switching and tick the check box

This will disable user switching.  I want to be able to switch users, just not from the logout applet in Xfce.

---

