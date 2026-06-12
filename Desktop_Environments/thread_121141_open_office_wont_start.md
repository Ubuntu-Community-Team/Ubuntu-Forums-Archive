---
title: "open office wont start"
date: 2006-01-24
forum: Desktop Environments
---

### Post by Karlos on 2006-01-24
when I try to fire up open office 2 nothing happens.
so I tried starting it via a terminal. This is what it echoed back to me.

karlos@greenstreet:~$ /usr/bin/oodraw2
[Java framework] Error in function createUserSettingsDocument (elements.cxx).javaldx failed!
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
/usr/lib/openoffice2/program/soffice: line 233:  7127 Aborted                 "$sd_prog/$sd_binary" "$@"
karlos@greenstreet:~$

this is only effecting one user (me)
it works fine for all the other users on this machine

I do remember setting the Java enviroment path in the settings to the java1.5 version which I installed with automatix. and it started happening after that.

any thoughts would be much appreciated.

---

### Post by rjwood on 2006-01-24
arnieboy also has a thread for removing programs installed by automatix. You may want to see if you could use that thread to uninstall and reinstall java or just change the settings/path. Search 'automatix' and find the thread..

---

### Post by Karlos on 2006-01-24
fixed:  I just deleted the .openoffice.org2 directory from my home directory and now it works fine.  Like you say tho I will check out the java problem and post my findings

---

