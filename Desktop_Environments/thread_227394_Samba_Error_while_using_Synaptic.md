---
title: "Samba Error while using Synaptic"
date: 2006-08-01
forum: Desktop Environments
---

### Post by MikeMLP on 2006-08-01
I've gotten this error the last few times I've used Synaptic.  The system appears to run fine, and updates appear to get installed, but this error really bothers me.  I wonder if anyone can tell me what is going on here, and what I should do about it (if anything).

The following is what I get in the terminal under synaptic.  Synaptic also pops up an error message in a window to let me know that something is fubar.

I've included the entire output here, so some of the terminal entries are just for synaptic's installation of the programs that I was trying to install at the time.  

```
(Reading database ... 132555 files and directories currently installed.)
Preparing to replace firefox-gnome-support 1.5.dfsg+1.5.0.5-0ubuntu6.06 (using . ../firefox-gnome-support_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace libnspr4 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06 (using ... /libnspr4_2%3a1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb) ...
Unpacking replacement libnspr4 ...
Preparing to replace libnss3 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06 (using .../ libnss3_2%3a1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb) ...
Unpacking replacement libnss3 ...
Preparing to replace firefox 1.5.dfsg+1.5.0.5-0ubuntu6.06 (using .../firefox_1.5 .dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb) ...
Unpacking replacement firefox ...
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Setting up libnspr4 (1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1) ...

Setting up libnss3 (1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1) ...

Setting up firefox (1.5.dfsg+1.5.0.5-0ubuntu6.06.1) ...

Setting up firefox-gnome-support (1.5.dfsg+1.5.0.5-0ubuntu6.06.1) ...

Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102 
```

I'd really appreciate a few words to sort this out.

Thanks a bunch!

---

### Post by MikeMLP on 2006-08-08
Bump!

This error occurs every time I try to install a package no matter the method.

Additionally, this error causes my machine to fail a "system sanity check." Packages that run this check cannot be installed (such as EasyUbuntu).

Any help would be appreciated.

---

### Post by MikeMLP on 2006-08-08
Update: as this seems to be a samba-only problem, I tried to uninstall samba.  Unfortunately, this error prevents synaptic from being able to remove samba from my system.  Does anyone have any advice on how to remove misbehaving packages?

---

### Post by DarthTibault on 2006-08-19
Same problem here...
Come on guys, there's got to be someone with a solution?

EDIT:
OK, I really need to learn to search a little further first... I found the fix:

```
sudo rm /etc/rc3.d/K09samba
sudo rm /etc/rc2.d/K09samba

sudo apt-get remove samba
sudo apt-get install samba
```

---

