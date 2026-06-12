---
title: "boot ubuntu without start X"
date: 2006-09-04
forum: Desktop Environments
---

### Post by hraposo on 2006-09-04
How I boot ubuntu without start X

---

### Post by anaconda on 2006-09-04
if you boot to recovery-mode (select from grub) then it wont start X.

You could also make a new entry to /boot/grub/menu.lst with a different runlevel (boot argument 0-9 ?? or something).. can't remember wich runlevels boot without x, but some of them do.

Sorry. can't be of more help.

---

### Post by foolsh on 2006-09-04
do you mean you want to boot up to the console?
and not the gdm or kdm login manager

to do this you can edit the startup script /etc/init.d/gdm or kdm "ubuntu or kubuntu respectively"

```
sudo gedit /etc/init.d/gdm
```

and add 
```
exit 0
```
to the second line
this will however prevent the login manager from running 
you can start the xserver after you have logged in with  
```
startx
```
but every boot will be to the console login screen

---

### Post by skymt on 2006-09-04
No! Don't edit the gdm script! There's a better way:
```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf --level 026 gdm off
```

---

