---
title: "Links in Xchat only open Konqueror"
date: 2006-09-26
forum: Desktop Environments
---

### Post by Devilotx on 2006-09-26
Links in Xchat used to open a new tab in Swiftfox, but all of a sudden, now links open new instances of Konqueror.

Running Dapper with Gnome/KDE installed.  

this is in Gnome

checked out gconf-editor and I didn't even see Xchat in there.

Seems to be related to the last Xchat update I got from apt.

---

### Post by CarpKing on 2006-09-28
I'm having this trouble as well.  I'm using Ubuntu Dapper with Konqueror and Amarok as the only KDE apps installed.

---

### Post by CarpKing on 2006-10-01
Solution found!  

[https://launchpad.net/distros/ubuntu/+source/xchat/+bug/61243](https://launchpad.net/distros/ubuntu/+source/xchat/+bug/61243)

Basically, just run ```
sudo update-alternatives --config x-www-browser
```
and change it to Swiftfox.  Not sure what all else it will affect, but I don't really want Konqueror to default for anything.

---

### Post by t3ddyg on 2006-10-24
I was having this aggrevating issue, and I just want to confirm
```
sudo update-alternatives --config x-www-browser
```
worked for me.  Now, my links launch in swiftfox =]

---

