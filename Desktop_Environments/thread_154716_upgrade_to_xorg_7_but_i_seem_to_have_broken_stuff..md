---
title: "upgrade to xorg 7 but i seem to have broken stuff..."
date: 2006-04-03
forum: Desktop Environments
---

### Post by Choad on 2006-04-03
it no longer starts x

at the end of the error report says it can not load the modules for fglrx, kbd and mouse or something like that...

one of them was the ati driver and the other 2 were just generic drivers for the keyboard and mouse

whassup with this? i have searched the forum but there suprisingly doesnt seem to be any kid of howto i can find...


oh by the way i am using a dapper flight 5 cd as my repository, and to upgrade i used synaptic to upgrade my xserver-xorg to version 7, and let it handle the dependancies how it wanted to.

---

### Post by vruum on 2006-04-03
are you trying to install the dapper xorg package on breezy? the change to 7 was a pretty big one, and a lot of things have been moved around, so while it's probably doable, and since you already got the dapper cd, it'll be a lot easier to upgrade your whole system to dapper.

---

### Post by Choad on 2006-04-03
great minds

sudo apt-get upgrade is underway :)

(why didnt i just install dapper to begin with? i dunno....)

---

