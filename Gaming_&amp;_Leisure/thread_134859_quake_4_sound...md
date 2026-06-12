---
title: "quake 4 sound.."
date: 2006-02-22
forum: Gaming &amp; Leisure
---

### Post by darknightuk on 2006-02-22
Hi i've installed quake4 at first i got a seg fault but fixed this by installing libsdl2.1debian-oss but i get no sound so i added +set s_driver oss to the startup script but seems to do nothing but if i start from console with quake4 +set s_driver oss i get sound?

#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/quake4"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
./quake4.x86 +set s_driver oss $*
exit $?

EDIT:-just noticed if i drag the icon off the menu i get sound but not if i launch the icon from the menu WTF:mad:

---

### Post by cdsboy on 2006-02-26
have you tried running it in the terminal as root. linux can be funny some times and it always helps to try that.

---

### Post by Adrian_b on 2006-02-26
It could be about something that your user doesn't have sound rights (isn't placed in the sound group), so try it in root..

---

### Post by cdsboy on 2006-02-26
ya that is what i was thinking. good to know someone else agrees with me

---

### Post by deathbyswiftwind on 2006-02-26
enter in terminal quake4 +set s_driver oss

---

