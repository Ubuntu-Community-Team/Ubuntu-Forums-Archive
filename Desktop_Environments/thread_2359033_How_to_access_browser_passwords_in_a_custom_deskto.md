---
title: "How to access browser passwords in a custom desktop session?"
date: 2017-04-20
forum: Desktop Environments
---

### Post by again? on 2017-04-20
I am using Ubuntu 16.04.
I created a custom compiz session as in this [**article**]("http://www.webupd8.org/2012/02/how-to-create-standalone-compiz-session.html").

I added these to my startup script
```
/usr/bin/gnome-keyring-daemon --start --components=secrets &
/usr/bin/gnome-keyring-daemon --start --components=pkcs11 &
/usr/bin/gnome-keyring-daemon --start --components=ssh &
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
```

The login.keyring is unlocked but chrome doesn't autofill my saved passwords.
The passwords were saved in my Ubuntu session and chrome password autofill works in this session and my xfce session.

What startup component do I need to add to make this work in my custom session.
This is my full ~/.compiz-session file.
```
#!/bin/bash

tint2 &
conky &
plank &
easystroke &
kupfer --no-splash &
glipper &
nm-applet &
nautilus -n &
get-ip-loop &
redshift-gtk &
altyo --id=org.gtk.altyo &
xdg-user-dirs-gtk-update &
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
/usr/bin/gnome-keyring-daemon --start --components=secrets &
/usr/bin/gnome-keyring-daemon --start --components=pkcs11 &
/usr/bin/gnome-keyring-daemon --start --components=ssh &

sleep 3
volumeicon &
megasync &
```

---

