---
title: "Starting X automatically"
date: 2007-08-02
forum: Desktop Environments
---

### Post by Darkfoxx on 2007-08-02
I just finished setting up a 7.04 machine to run as a Firefox kiosk. Everything works fine, except for the fact that I have to log in at the command line and type "startx".

Any way to automate this so that I press the power button on the machine, it boots as usual , then logs into "kiosk" and loads X automatically?

I have a script in place that I thought would do this for me. It looks like this:
```
#!/bin/bash
# this is /bin/startkiosk.sh
su - kiosk -c 'xinit'
shutdown -r now

```

That gets called from /etc/init.d/kiosk

Shouldn't it do what I want?

---

### Post by Darkfoxx on 2007-08-04
Bump :(

---

### Post by pointone on 2007-08-04
I completed a kiosk project this past winter and did the following for starting X:

Edit /etc/event.d/tty1 and change the last line to read:

```
exec /sbin/getty /usr/local/bin/kioskrespawn.sh 38400 tty1
```

With kioskrespawn.sh:

```
#! /bin/bash

PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/bin/X11

cd /

rm -rf /home/kiosk/
tar -xzf /usr/local/share/kiosk.tar.gz

su --command="startx" kiosk
```

The kiosk.tar.gz simply contained a pristine /home/kiosk/ folder so after every user logged off, X would restart, and the kiosk user's settings would be reset.

If using my method of editing tty1, you probably don't need the "shutdown -r now" in your script; using /sbin/getty will continuously respawn it.

---

