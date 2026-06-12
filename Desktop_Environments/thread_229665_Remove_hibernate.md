---
title: "Remove hibernate?"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Cable on 2006-08-04
Is there a way to remove the "Hibernate" option from the shut down menu?  It does not work on my computer, so there is no point in having it there.

---

### Post by bpreindl on 2006-08-15
Hi,

I'd also like to remove the Hibernate-Button and even more completely disable ACPI-functions for any user (also by using cli-tools).

In my case I run Ubuntu-Desktop remotely in an LTSP (Linux Terminal Server Environment) environment. When users are allowed to call ACPI-functions, they (in the hibernate button's case) shutdown my whole server (!!) remotely (and 20 other X-Sessions also) - even if they don't have extra permissions.

So how can I completely disable ACPI in Gnome / Ubuntu?

Thank you!

Bastian

---

### Post by Macchi on 2006-08-15
I am also looking for a way to remove hibernate as an option from my desktop application server running Ubuntu Dapper. It is not desirable for remote users to be allowed to shut it down. 


A  partial solution is to disable the options for shutdown or restart on the login screen and at the quit option of the system menu. 
On Gnome this is accomplished easily through: 
"System"->"Administration"->"Login Window", on tab "Local" unmark the box "Show Actions menu". Then users will not be given the option to shut down or restart. 


I still what to find a better solution. KDE has an option to require administrative rights for shutdown, restart, and other power management alternatives.

---

### Post by kenzu on 2006-08-22
run ```
$ sudo gconf-editor
``` 
go to *apps -> gnome-power-manager -> can_hibernate* uncheck that and your hibernate button is gone.

Kenzu

---

### Post by Cable on 2006-08-22
> **kenzu said:**
> run ```
$ sudo gconf-editor
``` 
go to *apps -> gnome-power-manager -> can_hibernate* uncheck that and your hibernate button is gone.

Kenzu

Perfect.  Thank you very much!

---

### Post by iputz on 2007-01-12
This does absolutely nothing for me in Ubuntu Edgy. Are you sure that's all there is?

---

### Post by tmatt95 on 2007-01-12
> **iputz said:**
> This does absolutely nothing for me in Ubuntu Edgy. Are you sure that's all there is?
One reason for it not working, is leaving in the "$" sign at the beginning of the instruction. To make the command run, you will have to remove the leading "$" and any spaces after/ before it. Below is a copy of the code, copied from Kenzu's post, with the offending dollar sign removed:

sudo gconf-editor

Regards,
Matt

---

### Post by iputz on 2007-01-12
The dollar sign I understand is only the command prompt---not the part of the actual command used to launch the gconf-editor. I can launch the editor, but when I uncheck the aforementioned option and quit the editor, the "hibernate" button still remains in the System --> Quit... dialog.

---

### Post by iputz on 2007-01-23
Ping to the top

---

### Post by Pobega on 2007-01-23
If anyone using Xfce/Xubuntu is wondering, the Hibernate button was removed from the Xfce equivalent menu in 4.4 stable.

I have no answer for Gnome/Ubuntu though.

---

### Post by explicitly ambiguous on 2008-06-19
Command should be

```
gconf-editor
```

and not

```
sudo gconf-editor
```

if you want to edit the current users options (sudo gconf-editor edits roots preferences).

Andrew

---

### Post by iputz on 2008-06-20
> **explicitly ambiguous said:**
> 
if you want to edit the current users options (sudo gconf-editor edits roots preferences).


How does one edit global preferences? Is there some config file I can edit to disable hibernation an/or suspend for all users?

---

