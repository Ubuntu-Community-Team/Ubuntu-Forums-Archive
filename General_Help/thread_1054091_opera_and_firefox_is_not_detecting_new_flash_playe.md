---
title: "opera and firefox is not detecting new flash player installation"
date: 2009-01-29
forum: General Help
---

### Post by nitish_nit555 on 2009-01-29
I am using ubuntu 8.04.

I have uninstalled older version of adobe flash player 9...

and than installed flash player 10.

but neither firefox nor opera is able to detect it.

help!!!!!!!!!

---

### Post by carlos.pereira on 2009-01-29
try this

sudo apt-get install adobe-flashplugin

---

### Post by scouser73 on 2009-01-29
The way I check to see whether I have the latest flash installed is to visit the Adobe site: [http://get.adobe.com/flashplayer/?promoid=BUIGP]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

A dialogue box will appear, it will either let you install the latest version or tell you that you are currently running the latest version.

---

### Post by nitish_nit555 on 2009-02-06
Please help........

I am getting the following error when trying to open youtube in firefox:




```
nitish@nitish-desktop:~$ firefox
LoadPlugin: failed to initialize shared library /usr/lib/adobe-flashplugin/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /home/nitish/.mozilla/plugins/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/adobe-flashplugin/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

```

---

### Post by nitish_nit555 on 2009-02-06
finally I have solved my problem :

[http://ubuntuforums.org/archive/index.php/t-969667.html:popcorn:](http://ubuntuforums.org/archive/index.php/t-969667.html:popcorn:)

---

