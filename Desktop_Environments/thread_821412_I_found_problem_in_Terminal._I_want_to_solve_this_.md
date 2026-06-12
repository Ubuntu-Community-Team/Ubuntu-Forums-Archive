---
title: "I found problem in Terminal. I want to solve this promblem. Can you help me please?"
date: 2008-06-07
forum: Desktop Environments
---

### Post by aurora_consurgens on 2008-06-07
I found this problem when I am installing program in Terminal. How can I solve this problem? Thank you

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=73247&stc=1&d=1212835724[/IMG]

---

### Post by mick222 on 2008-06-07
explain the problem

---

### Post by aurora_consurgens on 2008-06-07
Ok, When I am installing .deb file or update programs. It will show error message box but I can install or update program success and I think cause is Tuxguitar that I installed.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=73250&stc=1&d=1212837391[/IMG]


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=73251&stc=1&d=1212837391[/IMG]

---

### Post by forger on 2008-06-07
why don't you install easytag from menu Applications > Add/Remove ?

You installed timidity from somewhere, it broke the installation, looks like it's unstable (?)

try this in gnome terminal:
```
sudo dpkg -P timidity
sudo apt-get -f install
sudo apt-get update
sudo apt-get install --reinstall tuxguitar

```

My ubuntu only has a package "tuxguitar", no "tuxguitar-alsa" and "tuxguitar-oss"

---

