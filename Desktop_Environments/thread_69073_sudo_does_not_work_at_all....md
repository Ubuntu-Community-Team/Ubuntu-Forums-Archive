---
title: "sudo does not work at all..."
date: 2005-09-25
forum: Desktop Environments
---

### Post by buqingzi on 2005-09-25
Every time I type "sudo ..." at the Terminal, I get:
"sudo: unable to lookup [myhostnamehere] via gethostbyname()
 Password:postdrop: warning: unable to look up public/pickup: No such file or directory"

I am a first time user of linux, and I haven't changed anything yet "out of box". I get the message "Could not look up internet address for [myhostnamehere]. This will prevent GNOME from operating correctly. It may possible to correct the problem by adding [myhostnamehere] to the file /etc/hosts." But how I can do that if I can't "sudo gedit /etc/hosts"?
This is just for a standalone laptop that occasionly connects to the net by dialup. During setup I gave the hostname "ubd492ada" (just something random). Is that what's causing the problem?

Any help would be greatly appreciated. My apologies if this is too n00b...

---

### Post by Xian on 2005-09-25
Select the option to enter into recovery mode at the boot screen.
This will get you to a command prompt with admin priviledges.

You can then edit your hosts file with a terminal editor.

```
$ nano -w /etc/hosts
```
Ctrl+x to save, then 'y' to confirm.
ENTER to quit the session.

---

### Post by mlomker on 2005-09-25
> But how I can do that if I can't "sudo gedit /etc/hosts"?


Try typing **su** and use your regular password.

---

### Post by buqingzi on 2005-09-28
Thanks that worked perfectly!

[QUOTE=Xian]Select the option to enter into recovery mode at the boot screen.
This will get you to a command prompt with admin priviledges.
You can then edit your hosts file with a terminal editor.
```
$ nano -w /etc/hosts
```
Ctrl+x to save, then 'y' to confirm.
ENTER to quit the session.[/QUOTE]

---

