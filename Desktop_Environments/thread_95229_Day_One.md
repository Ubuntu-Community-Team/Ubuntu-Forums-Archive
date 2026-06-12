---
title: "Day One"
date: 2005-11-26
forum: Desktop Environments
---

### Post by daacon on 2005-11-26
Hello all 

For a change I thouhgt I would post some good news :eek: I installed Ubuntu today on a 4 year old PIII 1.7 Mhz and it went relativley smooth. (downloaded ISO from web site and burnt to cd with Nero) 

Only issues I had was getting Disk Manager to reconize my second disk. Took some tweaking (and searching these forms ) and editing /etc/fstab but we are good to go !

I plan on running an Oracle db on this server , so far very slick Install - not sure on no root and  having to "sudo" all commands. Will review the installation doc for Oracle see if I can carry on without a root user. 

Will have to look a the groups as I don't like secure all mount points 777 even if it is an internal server. 

Should mention - lots of experience with Unix (Solaris / IBM / HP-UX / Red HaT AS 2.X / Mandrake ) still the installation was slicker than Windoze - it reconized everything most imppressed so far. 

later...............dy

---

### Post by invalid on 2005-11-26
[QUOTE=daacon]not sure on no root and  having to "sudo" all commands. Will review the installation doc for Oracle see if I can carry on without a root user.[/QUOTE]
It is possible to activate the root account with
```
sudo passwd root
```
followed by a root password.

Cheers,
Cb

---

### Post by aysiu on 2005-11-26
For some of the pros and cons of using sudo (as opposed to root), read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by daacon on 2005-11-26
[QUOTE=aysiu]For some of the pros and cons of using sudo (as opposed to root), read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]

umm lot of good points - may have to unlearn some old habbits hahahah - I am root beware :rolleyes:

---

### Post by daacon on 2005-11-26
[QUOTE=invalid]It is possible to activate the root account with
```
sudo passwd root
```
followed by a root password.

Cheers,
Cb[/QUOTE]

thanks may use that may not ....it is a development box so worst case is nuke and redo that aleviates allot of pressue for sure ....

---

