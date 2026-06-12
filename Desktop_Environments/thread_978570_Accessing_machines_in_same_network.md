---
title: "Accessing machines in same network"
date: 2008-11-11
forum: Desktop Environments
---

### Post by pvpkiran on 2008-11-11
Hi all,
  I wanted to access an other machine in the same network to copy some shared folder .

 In windows i would use to do it like this
    Windows--->run--->\\<ipaddress of the machine>

How would i do the same in Ubuntu ? 
And also does the way i access depends on the OS of the machine im going to access(Ex: if the machine i want to access has windows or Ubuntu)

Thanx

---

### Post by habl on 2008-11-11
The easiest way is going to places -> connect to server. Select the method you would like to use at 'Service type', so for a Windows machine, you can select 'Widows share'. For linux machines it differs, but you probably want to use SSH.

And I think it's also possible to try ALT+F2 and type smb:/hostname/

And yes, it depends on the OS how you connect, not every OS use the same method.

---

