---
title: "can not run any admin tasks"
date: 2006-10-09
forum: Desktop Environments
---

### Post by Draaku on 2006-10-09
I am running a dual boot system windows/ubuntu. everything has been working fine with no problems until this monring. I logged in to ubuntu and saw that there were updates, when i clicked the icon and entered my sudo password it doesnt launch the updater. So I thought I would try going to System-Administration-Update Manager, enter my sudo password, again nothing. it seems it trys to launch but then fails. another thing i tried was from Terminal: 
```
fg32@ucc123:~$ sudo apt-get update
Password:
Password:
```

Why does it ask for my password twice? I think this is the problem, but i dont know where to begin. anyone experience this?

---

### Post by bswilson on 2006-10-09
> **Draaku said:**
> Why does it ask for my password twice? I think this is the problem, but i dont know where to begin. anyone experience this?

I have seen that before, when a person has incorrectly configured the ```
/etc/sudoers
``` file.  Have you made any system modifications recently?

---

### Post by Draaku on 2006-10-09
I also ran the script to convert to Christian Ubuntu.
I added my username to the file, trying to fix this problem. here is the file:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults    !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
fg32    ALL=(ALL) ALL
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by taurus on 2006-10-09
Do you belong to both groups adm & admin in /etc/group?

```
id
```

---

### Post by Draaku on 2006-10-09
Yes.

```
fg32@ucc123:~$ id
uid=1000(fg32) gid=1000(fg32) groups=4(adm),20(dialout),24(cdrom),25(floppy),29( audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(f g32)

```

---

### Post by Draaku on 2006-10-09
When I enter this command: sudo update-manager i get this: ```
fg32@ucc123:~$ sudo update-manager
Password:
Password:

```

running update manager from gui does not work, nor any other admin app. please does anyone know if there is a fix?

---

### Post by Draaku on 2006-10-10
anyone have any ideas?

---

### Post by taurus on 2006-10-10
See what happens if you run this from a terminal!

```
gksudo gedit
```

---

### Post by Draaku on 2006-10-11
```
fg32@ucc123:~$ gksudo gedit
fg32@ucc123:~$

```

The password window comes up, i enter my password, then it returns to the terminal prompt.

---

