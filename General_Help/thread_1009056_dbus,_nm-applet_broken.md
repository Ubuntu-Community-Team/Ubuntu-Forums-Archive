---
title: "dbus, nm-applet broken?"
date: 2008-12-12
forum: General Help
---

### Post by ameisevinyl on 2008-12-12
Hi folks,

i stumbled into an annoying bug (?) these days:
for some reasons (getting a rt-kernel to work)
i tried to stop several services with the
gnome-app "services" which comes with ubuntu.
i stopped all the apci, braille, alsa and:
DBUS!
actually i don't like dbus because of its ugly name
but then i thought, well dbus seems to be pretty
useful and i switched it on again.

but now:
whenever i start the system it loads gdm
but i cannot use mouse and keyboard so that i can't login

i switched to a console and there: keyboard works
so i started dbus manually (/etc/init.d/dbus restart)
and keyboard and mouse worked under X.

but now: nm-applet won't show up,
NetworkManager is running and also nm-applet but
it does not show up on the panel, sametime
it seems not to work, as it does not configure
my network interfaces automatically

which is also very annoying.

i guess that it needs also dbus running before
it get's loaded so that might be the fault

but i don't now how to fix this.
and i really just switched dbus of for one session
and than switched it on again a few minutes later,
leaving my system broken.

any help would be lovely!
thanks
mart

---

### Post by iponeverything on 2008-12-12
Give wicd a try =- it might be better choice in your circumstances. I think the post-install script in wicd takes are disabling NM to prevent conflicts.

---

