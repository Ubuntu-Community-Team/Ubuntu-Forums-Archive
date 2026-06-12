---
title: "Help installing VM"
date: 2005-05-25
forum: Desktop Environments
---

### Post by Chrisb319 on 2005-05-25
I tried installing LimeWire but I get that I do not have a VM. ](*,)

---

### Post by Chrisb319 on 2005-05-27
bump

---

### Post by 23meg on 2005-05-27
can you copy and paste the exact command you entered (if you entered one) and the exact error(s) you are getting? how exactly did you try installing limewire?

---

### Post by Chrisb319 on 2005-05-27
"sudo sh LimeWireLinux.bin"

then I get

"Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program."

Does this mean I have to install java because I have tried that.[The Manual](http://ubuntuguide.org/4.10/index.html#jre) says the file is called "jre-1_5_0_01-linux-i586.bin" and to download that but it's not there instead they have "jre-1_5_0_03-linux-i586.bin". I adjusted the file name acordingly but still when I try to install JRE when I get to "sudo gedit /etc/bash.bashrc"<-this command I get this.

"(gedit:6310): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

Isin't there an easier way to do this?

---

### Post by 23meg on 2005-05-28
try installing the j2RE package via apt if you haven't:

```
sudo apt-get install sun-j2re1.5
```

(you may need to [enable extra repositories](http://www.ubuntuguide.org/#extrarepositories).)

---

### Post by Chrisb319 on 2005-05-28
[QUOTE=23meg]try installing the j2RE package via apt if you haven't:

```
sudo apt-get install sun-j2re1.5
```

(you may need to [enable extra repositories](http://www.ubuntuguide.org/#extrarepositories).)[/QUOTE]

I'm still on the old warty, I already added extra repositories.

when i put in "sudo apt-get install sun-j2re1.5"

"Reading Package Lists... Done
Building Dependency Tree... Done
Package sun-j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2re1.5 has no installation candidate"

---

### Post by Chrisb319 on 2005-05-29
bump

---

### Post by Chrisb319 on 2005-06-04
bump.

---

