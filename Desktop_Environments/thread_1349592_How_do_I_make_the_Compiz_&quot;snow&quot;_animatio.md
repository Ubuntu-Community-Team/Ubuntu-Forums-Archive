---
title: "How do I make the Compiz &quot;snow&quot; animation start automatically?"
date: 2009-12-08
forum: Desktop Environments
---

### Post by fredbird67 on 2009-12-08
Technically, this is on Linux Mint Helena, but of course, that's based on Ubuntu Karmic, so I'm 99.44% sure the same instructions will apply here.  Anyways, I downloaded and installed the Compiz extras to get the "snow" animation on my desktop.  Yes, I'm in the Christmas mood and even have my "Merry Slickmas" GTK theme and "Christmas Remix" icon theme on here right now, both of which I created and can be found on GNOME-Look -- shameless plug, I know! LOL  In order to start the snow animation, I press Window-F3 to start it, but better yet, I would like to know if it's possible to have the snow animation automatically start when I log in.  Is this possible, and if so, how would I do that?

Thanx in advance,
Fred in St. Louis

---

### Post by dougrussell081869 on 2010-01-10
Well, this is an old post, but I was wondering the same thing and google didn't turn up any answers so I came up with a solution myself.  First off, I am running Gentoo with XFCE, but I doubt it matters.  I had the compiz DBUS plugin enabled and I created the following script, which I called toggle-snow...

```

#!/bin/bash
sleep 2
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/snow/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`

```Then I just have this script execute at login.  Maybe there is a more elegant solution, but this worked for me.

---

### Post by untrammelled on 2010-01-12
Here is a script that does not rely on dbus. It works by sending keystrokes to the desktop to toggle the snow plugin.

```
#!/bin/sh
# waiting for compiz to start
sleep 5
# starting snow
xsendkeycode 115 1;
xsendkeycode 69 1;
xsendkeycode 69 0;
xsendkeycode 115 0;
```You can run it from a terminal to check that it works. You can check that the keycodes are correct by running xev in a terminal and pressing/releasing the super (115) and F3 (69) keys.

To get the script to run at startup, add it to System -> Preferences -> Sessions with ```
Name: Start snow
``` and ```
Command: /bin/sh /full/path/to/mysnow.sh &
```If the snow does not start in a new session, you may need to change the time delay (5 seconds in the example above).

---

