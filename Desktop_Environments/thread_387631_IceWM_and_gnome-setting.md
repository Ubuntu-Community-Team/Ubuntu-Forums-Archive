---
title: "IceWM and gnome-setting"
date: 2007-03-18
forum: Desktop Environments
---

### Post by szymon_g on 2007-03-18
hi.
i've installed icewm via apt-get and i'm using it with thunar
i really like it's look :-)
but i've got a problem : i've got a laptop and i would like to use my 'special keys' freely (i mean keys fn + arrows or f8 for mute/unmute).
to have this i have to have a gnome-settings-daemon active. it's not hard to do that (application-sound-rhytmbox), but it's a little annoying to do that all the time :-/
is it possible to make it starting with icewm? i mean automatically :-)
i've tried to add it into startup file ( gnome-settings-daemon &&), i made this file executable (chmod +x startup), i've restarted computer and... nothing happened :-/

i'm using ubuntu 6.10 :-)

szymon

PS. sorry for my english :-)

---

### Post by Peter76 on 2007-03-18
It should work that way... Do you have the startup file in ~/.icewm? Check for a typo or something. Good luck

---

### Post by szymon_g on 2007-03-18
hm...
startup's location is valid ~./icewm
there is no misspelled inside of file :-/
but it's stil does'n work for me :-|

---

### Post by szymon_g on 2007-03-18
eh, 
i'm complatelly blind :-)
it should be only one & instead of && :-/
now it works :-)

---

