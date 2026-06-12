---
title: "New user Help!"
date: 2009-06-16
forum: General Help
---

### Post by Hinkhig on 2009-06-16
Hi,

I'm a new Ubuntu user just switching over from Windows and I'm looking for a bit of help.  I have Ubuntu installed on a VMWare machine and I am trying to install the VMWare Tools.  I am following the instruction when I try and install the tools using ./vmware-install.pl I get an error message back saying it needs to be run as a super user.

I am logged in on an account which should be an administrator what am I doing wrong?

Thanks,

---

### Post by Legace on 2009-06-16
Type **sudo** infront of the command :)

For example:
```
sudo mycommand options
```

In you case, it probably is something like:
```
cd /location/of/the/pl/file
sudo ./vmware-install.pl
```

For GUI apps, you should type gksudo:
```
gksudo gedit /etc/X11/xorg.conf
```

As a seperate note, check VirtualBox out. I prefer it to VMWare and you'll probably like it too ;)

---

### Post by eldragon on 2009-06-16
administrators dont have special powers by default.

if you wish to escalate to a super user for that script, run it with sudo
```

sudo name_of_script

```

check this page on the wiki: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Hinkhig on 2009-06-16
Thank you for your help.  I will check out Virtualbox as well, thanks for the tip.

---

### Post by Hinkhig on 2009-06-16
> **eldragon said:**
> administrators dont have special powers by default.

if you wish to escalate to a super user for that script, run it with sudo
```

sudo name_of_script

```

check this page on the wiki: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


Thanks for the help.

---

