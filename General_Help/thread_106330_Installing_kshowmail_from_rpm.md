---
title: "Installing kshowmail from rpm"
date: 2005-12-20
forum: General Help
---

### Post by lisigef on 2005-12-20
I downloaded the kshowmail rpm, used alien to convert it to a .deb file, and then installed it using 

sudo dpkg -i kshowmail_3.0.2-1_i386.deb 

It seemed to install correctly (no error messages) but when I type kshowmail I get 

bash: kshowmail: command not found

It does show up in Synaptic as installed via .deb file.

How do I run it?

Thanks,

-Lisi

---

### Post by mcmuffy on 2005-12-20
It may be that kshowmail is run by a different name or it is installed somewhere that is not in your run path (if this is the case someone else would have to explain how to add it).
To find out what files were installed and where select the propities icon in synaptic and it will give you the information you need.

---

### Post by lisigef on 2005-12-20
Here is what I get when I click on Installed files in Synaptic:
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/kshowmail
/usr/share/doc/kshowmail/copyright
/usr/share/doc/kshowmail/changelog.Debian.gz
/usr/share/doc/kshowmail-3.0.2
/usr/share/doc/kshowmail-3.0.2/AUTHORS
/usr/share/doc/kshowmail-3.0.2/ChangeLog
/usr/share/doc/kshowmail-3.0.2/TODO
/usr/share/doc/kshowmail-3.0.2/COPYING.gz
/usr/share/doc/kshowmail-3.0.2/INSTALL.gz
/usr/share/doc/kshowmail-3.0.2/README.gz
/opt
/opt/kde3
/opt/kde3/bin
/opt/kde3/bin/kshowmail
/opt/kde3/share
/opt/kde3/share/applnk
/opt/kde3/share/applnk/Internet
/opt/kde3/share/applnk/Internet/kshowmail.desktop
/opt/kde3/share/apps
/opt/kde3/share/apps/kshowmail
/opt/kde3/share/apps/kshowmail/kshowmailui.rc
/opt/kde3/share/apps/kshowmail/pics
/opt/kde3/share/apps/kshowmail/pics/eraser.png
/opt/kde3/share/apps/kshowmail/pics/kshowmail.png
/opt/kde3/share/apps/kshowmail/pics/kshowmail24.png
/opt/kde3/share/apps/kshowmail/pics/letter-closed.png
/opt/kde3/share/apps/kshowmail/pics/letter-open.png
/opt/kde3/share/apps/kshowmail/pics/ok.png
/opt/kde3/share/apps/kshowmail/pics/spam.png
/opt/kde3/share/apps/kshowmail/pics/tool.png
/opt/kde3/share/apps/kshowmail/sounds
/opt/kde3/share/apps/kshowmail/sounds/neuepost.wav
/opt/kde3/share/apps/kshowmail/sounds/newmail.wav
/opt/kde3/share/doc
/opt/kde3/share/doc/HTML
/opt/kde3/share/doc/HTML/de
/opt/kde3/share/doc/HTML/de/kshowmail
/opt/kde3/share/doc/HTML/de/kshowmail/index.cache.bz2
/opt/kde3/share/doc/HTML/de/kshowmail/index.docbook
/opt/kde3/share/doc/HTML/en
/opt/kde3/share/doc/HTML/en/kshowmail
/opt/kde3/share/doc/HTML/en/kshowmail/index.cache.bz2
/opt/kde3/share/doc/HTML/en/kshowmail/index.docbook
/opt/kde3/share/doc/HTML/es
/opt/kde3/share/doc/HTML/es/kshowmail
/opt/kde3/share/doc/HTML/es/kshowmail/index.cache.bz2
/opt/kde3/share/doc/HTML/es/kshowmail/index.docbook
/opt/kde3/share/doc/HTML/fr
/opt/kde3/share/doc/HTML/fr/kshowmail
/opt/kde3/share/doc/HTML/fr/kshowmail/index.cache.bz2
/opt/kde3/share/doc/HTML/fr/kshowmail/index.docbook
/opt/kde3/share/doc/HTML/sv
/opt/kde3/share/doc/HTML/sv/kshowmail
/opt/kde3/share/doc/HTML/sv/kshowmail/index.cache.bz2
/opt/kde3/share/doc/HTML/sv/kshowmail/index.docbook
/opt/kde3/share/icons
/opt/kde3/share/icons/hicolor
/opt/kde3/share/icons/hicolor/16x16
/opt/kde3/share/icons/hicolor/16x16/apps
/opt/kde3/share/icons/hicolor/16x16/apps/kshowmail.png
/opt/kde3/share/locale
/opt/kde3/share/locale/de
/opt/kde3/share/locale/de/LC_MESSAGES
/opt/kde3/share/locale/de/LC_MESSAGES/kshowmail.mo
/opt/kde3/share/locale/es
/opt/kde3/share/locale/es/LC_MESSAGES
/opt/kde3/share/locale/es/LC_MESSAGES/kshowmail.mo
/opt/kde3/share/locale/fr
/opt/kde3/share/locale/fr/LC_MESSAGES
/opt/kde3/share/locale/fr/LC_MESSAGES/kshowmail.mo
/opt/kde3/share/locale/sv
/opt/kde3/share/locale/sv/LC_MESSAGES
/opt/kde3/share/locale/sv/LC_MESSAGES/kshowmail.mo

I tried the ones that sounded like they might be executables, but I got 
lisi@Geffen:~$ /opt/kde3/bin/kshowmail
/opt/kde3/bin/kshowmail: error while loading shared libraries: 

and 

lisi@Geffen:/opt/kde3/share/apps/kshowmail$ sudo ./kshowmailui.rc
Password:
sudo: ./kshowmailui.rc: command not found
libmimelib.so.1:cannot open shared object file: No such file or directory

Ideas?

Thanks

-Lisi

---

### Post by mcmuffy on 2005-12-20
try '/opt/kde3/bin/kshowmail' at a command line and that should run it.
You may have to install libmimelib1a from synaptic though.

I have stuff that has installed there and has to be run that way. I think /opt/kde3/bin needs adding to your $PATH or something but I could be wrong.

---

### Post by lisigef on 2005-12-20
/opt/kde3/bin/kshowmail Gives me the error

/opt/kde3/bin/kshowmail: error while loading shared libraries: libstdc++-libc6.2 -2.so.3: cannot open shared object file: No such file or directory

I did install /opt/kde3/bin/kshowmail with apt-get but it didn't help, and there is no package libstdc++-libc6.2-2.so.3 to install. 

Next move? :)

Thanks!

---

### Post by Kuoi on 2007-04-24
I can't get it to work either.
I installed the converted rpm file and In Synaptic I only have these files installed...

--------------------------
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/kshowmail
/usr/share/doc/kshowmail/copyright
/usr/share/doc/kshowmail/changelog.Debian.gz
/kshowmail-3.1.2.tar.gz
/kshowmail.spec
------------

The deb file would not install because of an error : Dependency is not satisfiable kdelibs4c2a

kdelibs4c2a is installed , so don't know what the error means , but maybe it's because I use Feisty now ?

Can somebody help me to get Kshowmail to work ?
Kuoi

---

### Post by Kuoi on 2007-04-24
Maybe all can test this out , it works for me ...

I extracted the DEB file with fileroller to a folder I've /home/YOUR NAME/Kshowmail
Then I've extracted the 'control.tar.gz' and the 'Data.tar.gz' files in the same folder.

Now you can go with Nautilus to the folder "/home/YOUR NAME/Kshowmail/usr/bin"
In that folder you'll see a file "Kshowmail"
Rightclick on it and click on "make reference".
I've cut and pasted this reference to my Desktop , and till now Kshowmail does the job it's made for !

Kuoi

---

