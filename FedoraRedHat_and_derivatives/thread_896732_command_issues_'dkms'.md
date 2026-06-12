---
title: "command issues 'dkms'"
date: 2008-08-21
forum: Fedora/RedHat and derivatives
---

### Post by nnamdi on 2008-08-21
please am working on a project using Acronis after installation i am suppose to install ```
snapapi26_modules-0.7.39-1.noarch.rpm
```
in order to use it i have to issue commands when issue this command
```
# dkms ldtarball --archive=/usr/lib/Acronis/kernel_modules/snapapi26-0.7.39-all.tar.gz
```
it say ```
bash: dkms command not found
```

so i thought was an issue but when i 'man dkms' it gave a procedure meaning it is a command please what do i do, i am doing this on redhat enterprise server

---

### Post by cariboo on 2008-08-21
I can't help you with a problem in Redhat, but I can point you to this article about dkms:

[http://www.linuxjournal.com/article/6896](http://www.linuxjournal.com/article/6896)

Jim

---

### Post by nnamdi on 2008-08-22
hey friends i have fixed the issue on these i login in as root
```
su root
```then ran the command ```
#dkms ldtarball --archive=/usr/lib/Acronis/kernel_modules/snapapi26-0.7.39-all.tar.gz
```it work

or if you want to run it from user point 

login as root```
$su root
```then type```
#whereis dkms
```then ```
#su -c'/usr/sbin/dkms ldtarball --archive=/usr/lib/Acronis/kernel_modules/snapapi26-0.7.39-all.tar.gz'
```

this for redhat or RPM based distros

---

### Post by Oldsoldier2003 on 2008-08-22
Moved from ABT to Fedora/Redhat

---

