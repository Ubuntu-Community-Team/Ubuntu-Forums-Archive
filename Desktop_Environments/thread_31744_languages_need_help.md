---
title: "languages need help"
date: 2005-05-04
forum: Desktop Environments
---

### Post by marklar on 2005-05-04
Hi All,
Hear's the problem I need to be able to set up the PC in Canadian English and French 
ie: User A English, User B French. Englsh is default local, When I log in I select French
at login and recieve the error message "Language fr_CA.UTF-8 does not exist, using System default".
I have read and searched the Ubuntu site for help but no luck.
If their is documentation for this, point me and I will gladly read it before reposting here.
Thanks 
Marklar

---

### Post by bluefrog on 2005-05-04
sudo dpkg-reconfigure locales

then check all locales you need.

---

### Post by Alexander Kirillov on 2005-05-04
[QUOTE=marklar]Hi All,
Hear's the problem I need to be able to set up the PC in Canadian English and French 
ie: User A English, User B French. Englsh is default local, When I log in I select French
at login and recieve the error message "Language fr_CA.UTF-8 does not exist, using System default".
I have read and searched the Ubuntu site for help but no luck.
If their is documentation for this, point me and I will gladly read it before reposting here.
Thanks 
Marklar[/QUOTE]
 The only relevant info I could suggest is this:
 [http://www.ubuntulinux.org/wiki/LocaleConf](http://www.ubuntulinux.org/wiki/LocaleConf)
[http://www.ubuntulinux.org/wiki/GuideToHoary](http://www.ubuntulinux.org/wiki/GuideToHoary)

But the message "Language fr_CA.UTF-8 does not exist, using System default" can only mean one of two things: 
 - you have not installed some package which contains this language (possibly package "locales")
 - or there is a bug in Ubuntu, which should be reported and fixed. 

Please check whether you have locales package installed.

---

