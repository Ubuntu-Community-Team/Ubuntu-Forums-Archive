---
title: "Samba administration"
date: 2004-11-30
forum: Desktop Environments
---

### Post by artAlexion on 2004-11-30
With previous distros, I administered samba with SWAT.  apt/synaptic won't install SWAT because the version in the repository conflicts with the installed samba version.  What is the default means in Ubuntu to administer samba, create shares, mount windows shares to the file system, etc.?

---

### Post by jiyuu0 on 2004-12-01
I used the manual way...

Samba Server section
[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html)

---

### Post by bazuka on 2004-12-01
I also did it the manual way.  It's not too steep a learning curve for this.  I am not sure of any graphical tools for it though, unfortunately.

---

### Post by artAlexion on 2004-12-01
[QUOTE=jiyuu0]I used the manual way...

Samba Server section
[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html)[/QUOTE]
 I fould that document while trying to get mplayer and realplayer and Rhythmbox to work.  perused it and found the excellent smb.conf suggestions.  Samba working fine after I installed smbfs which is suprisingly not included in the base distro.

---

### Post by artAlexion on 2004-12-01
[QUOTE=bazuka]I also did it the manual way.  It's not too steep a learning curve for this.  I am not sure of any graphical tools for it though, unfortunately.[/QUOTE]
 I used to use SWAT, but it will not install on warty because it is an older version than the samba warty packages.  Runs in a web browser.  downloaded webmin-samba, but it won't take my password.  also tried TKSamba, a fine smbfs browser, but the mount functions don't seem to work.

---

