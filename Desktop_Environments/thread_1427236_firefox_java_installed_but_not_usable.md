---
title: "firefox java installed but not usable"
date: 2010-03-11
forum: Desktop Environments
---

### Post by coller_girl on 2010-03-11
i have java plug-in installed on firefox (Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.2pre) Gecko/20100310 Ubuntu/9.10 (karmic) Namoroka/3.6.2pre) on a Ubuntu 9.10 the Karmic Koala system with, gnome Version: 2.28.1 

i cannot load Java applets see the pictures 


[IMG]http://img715.imageshack.us/img715/7798/screenshot4q.png[/IMG]


any help getting java to work would be greatly appreciated - dunno how to --debug this or i would.

thanks
switch://girl

---

### Post by coller_girl on 2010-03-11
solved it was not finding the sys link so  mquin on freenode helped me link the plugins to firefox (firefox lost where they where)

with the following command

code:  ~$ sudo update-alternatives --install /usr/lib/mozilla/plugins/mozilla-javaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 1

---

