---
title: "kde is black out on log in in 9.10"
date: 2009-11-16
forum: Desktop Environments
---

### Post by sookun on 2009-11-16
Hi there,
im using gnome...wanted to see how kde works, installed it all fine but when i choose my session, the splash screen is ok, but cant see the desktop..its black out! i reversed kdm to gdm but it doesnt seem to work..
any help??

V

---

### Post by catach on 2009-11-16
I'm seeing the a similar (perhaps the same?) problem, tis quite odd.

I found that if I made a new user account I can use that to log in and KDE functions normally.

---

### Post by OrkanSpec on 2009-11-16
Hi,
I had also "black screen" after splash screen in KDE.
This was caused by a bug during changing KDE interface style from Oxygen to another.
Simplest solution is to remove .kde folder in you home: e.g. /home/YOUR_ACCOUNT/.kde. This will reset KDE settings for this user.

---

