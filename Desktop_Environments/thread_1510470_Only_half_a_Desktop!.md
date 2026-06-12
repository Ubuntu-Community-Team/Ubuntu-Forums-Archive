---
title: "Only half a Desktop!"
date: 2010-06-15
forum: Desktop Environments
---

### Post by earther on 2010-06-15
Has anyone ever had this happen to their Desktop?

[IMG]http://www.eartherdesigns.com/ss/desktop_position.jpg[/IMG]

Changing to a single Desktop in Compiz set things right.  Haven't tried resetting multiple Desktops yet . . .

---

### Post by earther on 2010-06-17
No comments on what might have caused this to happen?

---

### Post by angry_johnnie on 2010-06-17
your panel's in the right place, and it is nautilus taking care of the desktop.

you could try 

```
killall nautilus
```

it should start running again, on its own.

if it persists, you could set compiz to handle the desktop instead of nautilus (if you open ccsm you'll find 'wallpaper' somewhere).  Of course, allowing compiz to handle the desktop means you won't have any icons.

other than that... i don't know, i'm just guessing :p
try killing/restarting gdm

```
sudo /etc/init.d/gdm restart
```

or

```
sudo service gdm restart
```

depending on your version of ubuntu.  if you're using Hardy (according to the info under your avatar), it should be the first option.

---

### Post by earther on 2010-06-18
Thanks for your input.  It hasn't happened again but every so often a window (different aps) will jump almost off screen.  Very weird.  This never happened with Compiz on Gutsy.

---

