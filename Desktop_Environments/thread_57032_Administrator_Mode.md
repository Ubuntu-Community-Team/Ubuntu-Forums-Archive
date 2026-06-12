---
title: "Administrator Mode"
date: 2005-08-15
forum: Desktop Environments
---

### Post by x__dark on 2005-08-15
I'm trying to edit my Network Interfaces in KControl Module, but it requires I clikc the "Administrator Mode" button to make any changes. I click the button, enter the root pass and nothing happens. Is there something I'm doing wrong?

---

### Post by nad on 2005-08-15
If kubuntu is setup with sudo, it is expecting your password not the root password.

---

### Post by x__dark on 2005-08-15
it is, but the root pass and my pass are the same.

---

### Post by nad on 2005-08-15
Beats me!

Personally; vi /etc/network/interfaces  followed by /etc/init.d/networking restart  from a root terminal is all it takes.

---

### Post by fig_jam_uk on 2005-08-15
[QUOTE=x__dark]I'm trying to edit my Network Interfaces in KControl Module, but it requires I clikc the "Administrator Mode" button to make any changes. I click the button, enter the root pass and nothing happens. Is there something I'm doing wrong?[/QUOTE]

HI it sounds like administrator mode isnt working properly, i had this problem myself a while ago the way around this is goto a console window and type: sudo kcontrol 
then enter your password should load up kcontroll center with all oprions in administrator mode..

let me know if this works :)

---

### Post by GeneralZod on 2005-08-15
This is a well-known bug in Kubuntu (and possibly KDE in general...?).  It's cropped up numerous times on these forums e.g. [http://ubuntuforums.org/showthread.php?t=54104&highlight=kcontrol](http://ubuntuforums.org/showthread.php?t=54104&highlight=kcontrol).  Someone really should make a sticky about it :)

---

### Post by x__dark on 2005-08-15
Thanks a million, everything is running great now. Yes, this does seem like a big enough bug to have it's own little sticky. ;-)

---

### Post by zAo on 2005-08-15
The unofficial upgrade to KDE 3.4.2 makes it wrk though!

---

