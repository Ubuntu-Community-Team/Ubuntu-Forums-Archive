---
title: "Printer app disappeared from system settings"
date: 2016-12-29
forum: Desktop Environments
---

### Post by williepabon on 2016-12-29
Hi:
Turned on my machine this morning to find out that Printer app (the one that lets you add/delete/configure your printers) was not showing in the system settings window. I browsed /usr/share/applications and couldn't find it there, either. How can I recover it back? Thanks for any help.

My system:

```
williepabon@WP-Macmini:~$ uname -aLinux WP-Macmini 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
williepabon@WP-Macmini:~$ lsb_release -crid
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
williepabon@WP-Macmini:~$ 

```

wp

---

### Post by howefield on 2016-12-29
Can you check that system-config-printer-gnome is installed ?

```
apt-cache policy system-config-printer-gnome
```

---

### Post by williepabon on 2016-12-29
> **howefield said:**
> Can you check that system-config-printer-gnome is installed ?

```
apt-cache policy system-config-printer-gnome
```

**howefield:**

Thanks for answering. This is the code result:

```
williepabon@WP-Macmini:~$ apt-cache policy system-config-printer-gnomesystem-config-printer-gnome:
  Installed: (none)
  Candidate: 1.5.7+20160212-0ubuntu2
  Version table:
     1.5.7+20160212-0ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status
williepabon@WP-Macmini:~$ 
```

Below are the apps that show installed/uninstalled when I run synaptics package mgr. Here's the url for the picture:

[https://drive.google.com/open?id=0B_ZOUN6JcLCXdmpsa3pXakpmNjA](https://drive.google.com/open?id=0B_ZOUN6JcLCXdmpsa3pXakpmNjA)

wp

---

### Post by howefield on 2016-12-29
I'd suggesting installing it and checking if that populated system settings with the printer icon.

---

### Post by williepabon on 2016-12-29
**howefield:**
You solved my problem. Now I have my printer configuration app. Thank you very much.

wp

---

### Post by howefield on 2016-12-30
> **williepabon said:**
> **howefield:**
You solved my problem. Now I have my printer configuration app. Thank you very much.

wp

You're very welcome, thanks for marking the thread as solved.

---

