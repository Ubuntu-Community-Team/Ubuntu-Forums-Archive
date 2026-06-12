---
title: "Text is way too big in some apps! Karmic"
date: 2009-11-01
forum: Desktop Environments
---

### Post by systemshock869 on 2009-11-01
I just installed SMPlayer and the text for the menus, like File, view, etc. is gigantic! It makes it totally unusable.  Then I installed VLC media player, and it was the same way.  I remember having this same problem several months ago on a different installation of Xubuntu, with openoffice.  Can anybody give me any suggestions?  This shouldn't be happening on a mainstream distro..

---

### Post by systemshock869 on 2009-11-02
Can anybody help with this?

---

### Post by rvm4000 on 2009-11-03
Install qt4-qtconfig and run qtconfig.

It allows to customize the look of Qt applications (fonts and so on).

---

### Post by BambooClaw on 2009-11-05
I believe I have the same problem.  See attachment for what happens when I run qtconfig.  I am having the same problems with Virtualbox, I haven't tried any other qt based apps but I assume they are all having this problem.  Please help, are there any config files that can be manually checked/changed?

---

### Post by rvm4000 on 2009-11-05
I think the Qt settings are stored in $HOME/.config/Trolltech.conf

---

### Post by kelvin.illa on 2009-11-05
I've had the same problem: [http://ubuntuforums.org/showthread.php?t=1307316](http://ubuntuforums.org/showthread.php?t=1307316)

---

### Post by BambooClaw on 2009-11-07
I have had some success with fixing qt3 based apps.  I edited the file /etc/qt3/qtrc and changed the line:
font=Sans Serif,9,-1,5,50,0,0,0,0,0
to:
font=Sans Serif,1,-1,5,50,0,0,0,0,0

This has fixed for qt3 based apps (including the qtconfig-qt3 app).

Is there a similar setting for qt4 configuration?  (without using the qtconfig application)

---

