---
title: "Sound problem in ET 2.55 with Ubuntu 7.10"
date: 2007-07-09
forum: Gaming &amp; Leisure
---

### Post by Programmerer on 2007-07-09
I had Enemy Territory  2.55 installed on Ubuntu 7.04, and that worked fine, but when I upgraded to the beta version 7.10 were suddenly the sound death:(
I can hear sound when not playing ET, it is just in ET that the sound isn't working](*,)
I have tried both OSS and ALSA but didn't work. Checked also System>Preferences>Sound but nothing was wrong there. Also tried ET 2.60b, but no sound there either:confused:
Please help me[-o< because I don't want to Re-Install Ubuntu 7.04 just for to be able to play ET with sound.

---

### Post by FoolsGold_MKII on 2007-07-09
Open a terminal and run the following:

sudo gedit /etc/rc.local

Enter the following line somewhere BEFORE the 'exit 0" line in the file:

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

Save, reboot, enjoy. This will fix the sound evertime you run Linux, but if you want a preview without having to reboot, run the following in a terminal:

sudo bash
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit

Run et, enjoy.

---

### Post by Programmerer on 2007-07-09
> **FoolsGold_MKII said:**
> Open a terminal and run the following:

sudo gedit /etc/rc.local

Enter the following line somewhere BEFORE the 'exit 0" line in the file:

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss


Didn't work, this is the edited file(/etc/rc.local):
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit 0
```

Still no sound, it's only in et I gets that error:(

Any more suggestions?

Have also tried two scripts for to start ET:
```
#!/bin/bash
export ETSDL_SDL_LIB="libSDL.so"
cd /usr/local/games/enemy-territory/
LD_PRELOAD="/home/thomas/et-sdl-sound/et-sdl-sound.so" ./et.x86 $*
```
And:
```
#!/bin/bash
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
killall esd
et
esd
exit 0
```

---

### Post by Programmerer on 2007-07-12
OK, since I still can't hear any sound after upgraded to Ubuntu 7.04 then I'm gonna re-install Ubuntu.

Is this a bug in Ubuntu 7.10????

---

### Post by Programmerer on 2007-07-13
> **Programmerer said:**
> OK, since I still can't hear any sound after upgraded to Ubuntu 7.04 then I'm gonna re-install Ubuntu.


Well, now have I re-installed Ubuntu, and now is the sound working correctly. 


I hope this problem will be fixed!

---

### Post by holihue on 2007-10-21
Maybe you should try Gutsy.
And hope it only was a problem in beta version.

---

### Post by Sockerdrickan on 2007-10-21
lol bump :S

---

