---
title: "Where is $HOME/.dmrc?"
date: 2009-05-23
forum: General Help
---

### Post by carlosgs91 on 2009-05-23
.

---

### Post by sisco311 on 2009-05-23
[thread=976610]Solving .dmrc and $HOME Permission Errors[/thread]

---

### Post by cham93086 on 2009-05-23
Hi;

2 answers to your question:

**First**; .dmrc is found in your home directory.  if your looking in nautilus, you need to hit ctl-h to see hidden files.  If after doing that, it still isn't there, no sweat, don't worry about it.
  
**Secondly,** I had the same problem/error message, the solution is as follows; (with a step by step after)

In the directory /etc/gdm/ There is a file called gdm.conf-custom

in the Security section, you need to either add a line to read 

```
RelaxPermissions=2
```

then restart GDM.  
[B]
ok... step by step instructions[/B]

1) open a terminal

enter:

```
cd /etc/gdm
sudo gedit gdm.conf-custom
```

search the file for the "security" section.

enter or change a line to read 

```
RelaxPermissions=2
```

save it and exit

then, press ctl+alt+F1 (you need a "real" terminal)

login, then 

```
sudo killall gdm
sudo gdm
```

that should solve your problem.

I'm not quite able to explain why or how it works, but, I know it has something to do with the way GDM checks for permissions on login.

---

### Post by mcduck on 2009-05-23
..and after you get it fixed, never run graphical applications with "sudo" again. Use "gksudo" instead. ;)

(running GUI apps with sudo instead of gksudo is the most common reason for ownership/permissions of your files changing. Sudo isn't made for graphical applications and doesn't load root's environment correctly for them. So you end running as root but using your normal user's home & configuration files..)

---

### Post by carlosgs91 on 2009-05-24
.

---

### Post by overdrank on 2009-05-24
[RootSudo]("https://help.ubuntu.com/community/RootSudo") and the [Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201")

---

