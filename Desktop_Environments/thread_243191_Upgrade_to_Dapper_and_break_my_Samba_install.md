---
title: "Upgrade to Dapper and break my Samba install"
date: 2006-08-24
forum: Desktop Environments
---

### Post by WoodyMahan on 2006-08-24
In Synaptic I get error of "E: samba: subprocess pre-removal script returned error exit status 102"  when I try to uninstall Samba.  It is showing as broken and I get this error when I try to upgrade, remove or anything else.

---

### Post by peabody on 2006-08-24
Is there anything else it shows?  The only advice I have is that we can try to locate what the removal script doesn't like and see if we can hack something up that makes it satisfied.  Once that's done it should properly remove and we can install the new version.

---

### Post by WoodyMahan on 2006-08-24
It doesn't give me anything else.  But if I try to upgrade it I get this: "E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb: subprocess new pre-removal script returned error exit status 102"

Maybe someone knows a way to run the command that will return a more robust reply?

---

### Post by peabody on 2006-08-24
Are you updgrading within apt or synaptic?

Edit, blah, never mind you told me.  Try apt in a terminal, sudo apt-get upgrade.  Maybe it'll output more.

---

### Post by WoodyMahan on 2006-08-29
Never got this to work the way I wanted so I reformatted the HD and reinstalled.  Everything is pretty much back to normal.

---

### Post by paulyphonic on 2006-09-10
i am receiving the same problem with Samba. This is the output that i receive:

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ilmw on 2007-02-07
Please see the following topic:

[samba-common = 3.0.23d-4 but 3.0.24-2 is installed]("http://www.debianhelp.org/node/4073")

The method that Florian Kulzer provided works for me:

[B]cd /etc/rc2.d/
ln -sf ../init.d/samba K09samba[/B]

Good luck!

---

