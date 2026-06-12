---
title: "dpkg error HELP"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Nikku49 on 2006-08-02
ok i ran automatix and in the middle of it donwloading the fonts i lost internet connects. and it was timed out so i did a ctrl + c inside the screen to close it out. now every time i try to install something with dpkg it tries to install thoes fonts, but says failed: connection refuesed by host ( sourceforge ) and then it gives me an error about msttcorefonts couldnt be insttalled. i cant reinstall it becuase it tries to install thoes dang fonts. i tried doing dpkg --configure -a but it fails when tryin to reinstall the fonts. 

is there anyways i can get around this?

---

### Post by Nikku49 on 2006-08-02
kk i fixed it,
here is what i did
dpkg --purge msttcorefonts

wich removes the packaged wich was half installed on my system

---

