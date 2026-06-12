---
title: "Recurring errors..."
date: 2006-09-22
forum: Desktop Environments
---

### Post by Culito on 2006-09-22
I've been trying to install Samba and I can't get it to work.  Now there's a new Firefox/flash upgrade and it won't install either.  When I try to update, I get these errors:

cully@Culito:~$ sudo apt-get install samba
Password:
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 flashplugin-nonfree
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)


What do you guys/gals make of all this?

---

### Post by Sentinel83 on 2006-09-22
Culito,

I have had this problem before I believe.  Did you try to use EasyUbuntu or Automatix to install the new Flash plugin?  

I think this is due to the fact that the install for flash didn't finish, or is still waiting on license acceptance / user input.  For example, I had the same error and when I ran through the installs of the plugin I realized I skipped the "I agree" portion of the install.  This caused apt-get to hold onto that process until I cleared it by installing/accepting the license again.

---

### Post by arnieboy on 2006-09-22
> **Sentinel83 said:**
> Culito,

I have had this problem before I believe.  Did you try to use EasyUbuntu or Automatix to install the new Flash plugin?  

I think this is due to the fact that the install for flash didn't finish, or is still waiting on license acceptance / user input.  For example, I had the same error and when I ran through the installs of the plugin I realized I skipped the "I agree" portion of the install.  This caused apt-get to hold onto that process until I cleared it by installing/accepting the license again.

automatix will uninstall the buggy flash package from multiverse, and install flash from the adobe site. This will solve both the apt issue and install flash at one go.

---

### Post by Culito on 2006-09-22
I get the same errors through automatix.  And it gives me a 404 not found error when trying to download flash.

---

### Post by arnieboy on 2006-09-22
> **Culito said:**
> I get the same errors through automatix.  And it gives me a 404 not found error when trying to download flash.

interesting.. because I just checked and the link is working fine from AX.
I think the flash package in multiverse itself is causing trouble.
what does
```
sudo apt-get remove flashplugin-nonfree
```
give?

---

### Post by Culito on 2006-09-24
Well, the new flash update mysteriously installed itself correctly.  I don't even remember what I was doing, but it worked.  Still can't get Samba installed, though...


cully@Culito:~$ sudo apt-get install samba
Password:
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
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

