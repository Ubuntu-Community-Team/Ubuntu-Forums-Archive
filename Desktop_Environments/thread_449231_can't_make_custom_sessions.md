---
title: "can't make custom sessions"
date: 2007-05-20
forum: Desktop Environments
---

### Post by dbbolton on 2007-05-20
i created a file called '/usr/bin/startob.sh' which contains:
```
#!/bin/sh
gnome-settings-daemon &
perlpanel &
exec openbox
```after creating that file, i ran this command:
```
sudo chmod a+x/usr/bin/startob.sh
```next i created a file called '/usr/share/xsessions/obalt.desktop' which contains:
```
 [Desktop Entry]
Encoding=UTF-8
Name=Custom OB
Comment=Use this session to run Openbox as your desktop environment
Exec=/usr/bin/startob.sh
Icon=
Type=Application
```when i logged out of gnome, i went to "options" at the bottom-left corner of the login screen, and clicked "sessions".  below session 1 (which is gnome) there is a session called "foo", and no others. obviously, my custom session should be called "Custom OB". i tried to log in to "foo" anyway, but it gave me an error message, claiming that there was no exec line in some file.

what is going on here?

---

### Post by dbbolton on 2007-05-20
it turns out that, somehow, the first bracket [ was missing. my bad.

---

