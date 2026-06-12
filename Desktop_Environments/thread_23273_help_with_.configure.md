---
title: "help with ./configure"
date: 2005-04-01
forum: Desktop Environments
---

### Post by mdm4301 on 2005-04-01
Whenever I run ./configure to install a program I get the following error.

checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

I have installed the header files for my kernel through synaptic but that did not fix the problem.  What should I do?

---

### Post by mirtux on 2005-04-01
Hi,
  did you install the **kdelibs4-dev **package? I think is the main reason for not working....

Regards,
MC

---

### Post by fdoving on 2005-04-01
try to run configure with --prefix=/usr

---

### Post by mdm4301 on 2005-04-01
[QUOTE=mirtux]Hi,
  did you install the **kdelibs4-dev **package? I think is the main reason for not working....

Regards,
MC[/QUOTE]
 yeah that fixed it,  thanks alot for the help

---

### Post by mirtux on 2005-04-02
I'm happy that you managed to get it working! :wink:

Regards,
MC

---

### Post by rwabel on 2005-04-26
[QUOTE=mirtux]Hi,
  did you install the **kdelibs4-dev **package? I think is the main reason for not working....

Regards,
MC[/QUOTE]

I also tried to compile a kde program and run in the same problem. I then wanted to install kdelibs4-dev, but get dependency problems with my hoary.
[i]The following packages have unmet dependencies:
  kdelibs4-dev: Depends: libsasl2-dev but it is not going to be installed
E: Broken packages[/i]

and libsasl2-dev gives me that dependency problem:
[i]The following packages have unmet dependencies:
  libsasl2-dev: Depends: libsasl2 (= 2.1.19-1.5ubuntu1) but 2.1.20-0sherpya1 is to be installed
E: Broken packages[/i]

How did you guys install that or how can I solve that dependency problem

---

### Post by Fab on 2005-04-26
[QUOTE=rwabel]I also tried to compile a kde program and run in the same problem. I then wanted to install kdelibs4-dev, but get dependency problems with my hoary.
[i]The following packages have unmet dependencies:
  kdelibs4-dev: Depends: libsasl2-dev but it is not going to be installed
E: Broken packages[/i]

and libsasl2-dev gives me that dependency problem:
[i]The following packages have unmet dependencies:
  libsasl2-dev: Depends: libsasl2 (= 2.1.19-1.5ubuntu1) but 2.1.20-0sherpya1 is to be installed
E: Broken packages[/i]

How did you guys install that or how can I solve that dependency problem[/QUOTE]
 sounds like you have a non-ubuntu version of that package (libsasl2)
try uninstalling it and  then reinstall from the ubuntu repo (its in main afair)

---

### Post by rwabel on 2005-04-26
[QUOTE=Fab]sounds like you have a non-ubuntu version of that package (libsasl2)
try uninstalling it and  then reinstall from the ubuntu repo (its in main afair)[/QUOTE]

yes thanks a lot that was exactely the problem. I used once a special kde repository. I completely forgot that.
I've now downgraded all of them to ubuntu and works fine.
finally I can compile the kde programs

---

