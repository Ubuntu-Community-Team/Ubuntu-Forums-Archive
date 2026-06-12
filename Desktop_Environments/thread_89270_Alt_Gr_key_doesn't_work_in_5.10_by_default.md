---
title: "Alt Gr key doesn't work in 5.10 by default"
date: 2005-11-12
forum: Desktop Environments
---

### Post by mikko.ohtamaa on 2005-11-12
I installed Ubuntu 5.10 with US keyboard layout.

After installing, I switched keyboard layout to Finnish in Keyboard preferences. Scandinavian letters (åäö) worked, but Alt Gr key didn't. Alt Gr key is to used to type second symbol in non-alphabetic keys. E.g. Alt Gr + 2 produces @ in Finnish keyboard. Ubuntu is pretty much useless in everyday desktop usage if Alt Gr doesn't work.

Fiddling around in Keyboard preferences / layout options didn't help. However, this shouldn't needed. Alt Gr should be automatically actived when switching keyboard layouts (a usability issue).

Finally I found a cure to the problem. Type in following command to a terminal:
setxkbmap -layout fi 

Maybe Ubuntu conf  files or Gnome Keyboard preferences application are broken. This should be fixed ASAP since out-of-the-box experience is pretty bad for international people if they cannot type propeply.

Cheers,
MIkko Ohtamaa
Oulu, Finland

---

### Post by meborc on 2005-11-12
yeah, i had problems with estonian keyboard layout as well... it seemd like a lot of people were not happy about the keyboard settings GUI not functioning properly... after making some changes in conf files i got mine working OK, but i still can't use < and > button :rolleyes: , but i'm not a hard-core programmer, so i really don't give a **** :D 

there was a long discussion about 5.10 RC keyboard problems and we all hoped it could be fixed before 5.10 release... several bugs were reported, but it was too late i guess... only hope is that the dapper release is a bit more functional in that sence :D

---

### Post by katu on 2005-11-12
Had the same problem with he polish keyboard. In my case It seemed to be enough to uncheck the box in:
*preferences->keyboard->layout options->Groups shift/lock behaviour->"both alt keys together change group"*

The fact that this thing is on by default in keyboard layouts that need alt-gr is annoying though.

note: this is on an ubuntu system upgraded from hoary to breezy. I don't remember problems with kubuntu installed from scratch.
cheers,
Katu

---

