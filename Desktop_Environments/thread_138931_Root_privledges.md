---
title: "Root privledges"
date: 2006-03-02
forum: Desktop Environments
---

### Post by GQed76 on 2006-03-02
I used to be able naut via terminal as root user..i typed this in KDE with Konqueror and got some issues...any idea whats wrong?

gqed76@GQubuntu:~$ sudo konqueror
Link points to "/tmp/ksocket-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-9727' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KMimeType): WARNING: KServiceType::offers : servicetype Browser/View not found
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): ERROR: No database available!
kio (KMimeType): WARNING: KServiceType::offers : servicetype KonqAboutPage not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype KonqAboutPage not found
konqueror: WARNING: KonqFactory::createView : no factory
konqueror: WARNING: Profile Loading Error: View creation failed
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found

---

### Post by Jucato on 2006-03-02
have you tried using 
```
kdesu konqueror
```

---

### Post by GQed76 on 2006-03-02
that worked but i still get  errors...I wonder if my kde upgrade went bad

gqed76@GQubuntu:~$ kdesu konqueror
kbuildsycoca running...
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
Invalid entry (missing '=') at /tmp/kde-root/kconf_update432ejb.tmp:1
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_thumbnail: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_trash: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio (KDirWatch): WARNING: KDirWatch::removeDir can't handle '/etc/samba/smb.conf'
kio (KDirWatch): WARNING: KDirWatch::removeDir can't handle '/etc/security/fileshare.conf'
kio (KDirWatch): WARNING: KDirWatch::removeDir can't handle '/etc/security/fileshare.conf'
gqed76@GQubuntu:~$

---

### Post by Jucato on 2006-03-02
Is this a fresh install of Kubuntu? or kubuntu-desktop over an Ubuntu install? Could you also give the KDE version you are using?

---

### Post by GQed76 on 2006-03-02
It wa sa fresh install of Ubuntu, then I upgraded to KDE
then i upgraded that to 3.5.1

---

