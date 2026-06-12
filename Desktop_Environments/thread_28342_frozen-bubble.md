---
title: "frozen-bubble"
date: 2005-04-19
forum: Desktop Environments
---

### Post by lee_connell on 2005-04-19
no sound is coming from frozen-bubble game.  what can i do to try and fix this issue? do i have to turn off the esd sound startup option?

---

### Post by lukem on 2005-04-19
There must be a better way, but if you will type 

"killall esd"  

before you start frozen bubble it should have sound.  Once you finish playing frozen bubble ( if you can ever quit) you might want to restart esd

"esd"

Have fun

---

### Post by speedman on 2005-04-19
Edit /etc/esound/esd.conf as follows:

=====

[esd]

# -=CAH=- commented out following line
#auto_spawn=0

# -=CAH=- added following line
auto_spawn=1

# -=CAH=- commented out following line
#spawn_options=-terminate -nobeeps -as 5

# -=CAH=- added following line
spawn_options=-terminate -nobeeps -as 2 -d default

spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

=====

Log out of Gnome and back in again and you should be good to go.


Regards,

SM

---

### Post by maurom on 2005-04-19
There's a simpler solution that worked for me.

1) Enable universe repository
2) Run...

apt-get install libsdl1.2debian-all

This will remove (and then, replace) libsdl1.2debian-oss

That should work...

---

