---
title: "Move Gnome Panels From Command Line?"
date: 2010-07-31
forum: Desktop Environments
---

### Post by klausner on 2010-07-31
Is there a way to reposition the Gnome panels from the command line?

---

### Post by hariks0 on 2010-07-31
Try editing the gconf entry from terminal. I do not remember the exact key though.

---

### Post by klausner on 2010-08-02
> **hariks0 said:**
> Try editing the gconf entry from terminal. I do not remember the exact key though.

Any luck remembering the necessary key(s)? Or how to edit it from the CL?

---

### Post by hariks0 on 2010-08-02
Don't remember the exact keys. For editing gconf from terminal these threads may help :)

[http://ubuntuforums.org/showthread.php?t=1102761](http://ubuntuforums.org/showthread.php?t=1102761)
[http://ubuntuforums.org/showthread.php?t=979369](http://ubuntuforums.org/showthread.php?t=979369)
[http://ubuntuforums.org/showthread.php?t=1194932](http://ubuntuforums.org/showthread.php?t=1194932)

---

### Post by klausner on 2010-08-02
> **hariks0 said:**
> Don't remember the exact keys. For editing gconf from terminal these threads may help :)

Thanks. That's a start, But I still need to figure out the key names associated with the panels, and the values for moving them.

The reason I'm looking, is that I prefer to have both panels on the bottom of the screen, but Lucid insists on putting the panel with the widgets on top of the panel with the open windows (if that makes any sense). I want them the other way around, and I'm tired of doing it manually every time I log in. So I want to write a script to do it automatically.

---

### Post by hariks0 on 2010-08-02
In that case, why don't you just exchange the items in both panels each other? Is not it the easiest and logical way ?;)

---

### Post by mcduck on 2010-08-02
You'll really just have to check the panel names yourself with gconf-editor.

There's no way anybody could tell you what your panels are called, as it depends on how you might have created, moved and removed the panels over time. The keys for panel orientation are in apps/panel/toplevels/*name-of-the-panel*/orientation, and possible values are "top", "bottom", "left" and "right".

Also if you don't need the panels to be expanded you can simply define the exact locations for the panels as x and y coordinates relative to the screen, and they will stay in that place so you don't have to move them there at each login. What comes to expanded panels, they were never made to be used with more than one panel on each side of the screen, so the *will* keep on swapping places when both panels try to get to the screen edge.

---

### Post by klausner on 2010-08-02
> **hariks0 said:**
> In that case, why don't you just exchange the items in both panels each other? Is not it the easiest and logical way ?;)

Tried that. Moved all the content from one to the other, and so on. Ended up with the same problem :(

---

### Post by klausner on 2011-01-02
*Almost* have the answer. Thanks to the tips from [hariks0]("http://ubuntuforums.org/member.php?u=568207"), the syntax hint in [this thread]("http://ubuntuforums.org/showthread.php?t=1102761"), and lots of trial-and-error I figured out the handles for the panels, and the values I needed for them

In order to automatically set the locations where I want them, I wrote the following script:
```
sleep 60
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation top
audacious&
sleep 5
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation bottom
```

The long sleep at the beginning is to make sure that both panels have time to come up after a reboot. It's a bit excessive, but will tune it later.

The call to audacious is not because I want to play music, but to make sure the script runs.

If I run the script from the command line, it executes perfectly, and the results are as expected.

**[COLOR="Red"]BUT[/COLOR]**, if I call the script in the background from my ~,profile at login, the panels never move! The test call to audacious works fine, so I know the script executes, but the panel positioning is a bust. ](*,)

Anyone have any ideas?

---

### Post by Krytarik on 2011-01-03
I have a script to update/change the desktop background wallpaper, which stopped working after I upgraded from 7.10 to 10.04. At that time I found some workaround commands to add to the script, however I'm not sure if they are really necessary, because sometimes the script did also work without them. I post the whole script for clarity:```

#!/bin/sh

# Get the pid of nautilus
nautilus_pid=$(pgrep -u $LOGNAME -n nautilus)

# If nautilus isn't running, just exit silently
if [ -z "$nautilus_pid" ]; then
exit 0
fi

# Grab the DBUS_SESSION_BUS_ADDRESS variable from nautilus's environment
eval $(tr '\0' '\n' < /proc/$nautilus_pid/environ | grep '^DBUS_SESSION_BUS_ADDRESS=')

# Check that we actually found it
if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
#echo "Failed to find bus address" >&2
exit 1
fi

# export it so that child processes will inherit it
export DBUS_SESSION_BUS_ADDRESS

# delete original image
rm -f ~/Pictures/New_York.jpg
# get image and save in my HOME
wget -o /dev/null -q -t 3 -T 8 -O ~/Pictures/New_York.jpg http://wirednewyork.com/webcam/new-york-live.jpg
# reset background with a non-existent image
# if you don't use this, then next line will not update the wallpaper
gconftool -s -t string /desktop/gnome/background/picture_filename /usr/share/backgrounds/dummy.jpg
# load new desktop background image
gconftool -s -t string /desktop/gnome/background/picture_options centered
gconftool -s -t string /desktop/gnome/background/picture_filename ~/Pictures/New_York.jpg
# /usr/local/bin/alt-notify-send "Live-Cam:" "New York" applets-screenshooter
```

---

### Post by klausner on 2011-01-03
Maybe I'm missing the point, but I don't see how this applies.

---

### Post by Krytarik on 2011-01-03
> **klausner said:**
> Maybe I'm missing the point, but I don't see how this applies.
gconftool-2 apparently somehow don't work if run "off-screen", e.g. via crontab or startup scripts.

Try putting it this way:
```
#!/bin/sh
 
[COLOR=Red]sleep 60[/COLOR]

# Get the pid of nautilus
nautilus_pid=$(pgrep -u $LOGNAME -n nautilus)

# If nautilus isn't running, just exit silently
if [ -z "$nautilus_pid" ]; then
exit 0
fi

# Grab the DBUS_SESSION_BUS_ADDRESS variable from nautilus's environment
eval $(tr '\0' '\n' < /proc/$nautilus_pid/environ | grep '^DBUS_SESSION_BUS_ADDRESS=')

# Check that we actually found it
if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
#echo "Failed to find bus address" >&2
exit 1
fi

# export it so that child processes will inherit it
export DBUS_SESSION_BUS_ADDRESS

gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation top
audacious&
sleep 5
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation bottom
```
PS.: Delaying execution of the script for 10 secs should be sufficient.

---

### Post by klausner on 2011-01-03
So exporting DBUS_SESSION_BUS_ADDRESS allows gconftool-2 to work?

---

### Post by Krytarik on 2011-01-03
> **klausner said:**
> So exporting DBUS_SESSION_BUS_ADDRESS allows gconftool-2 to work?
It should.

---

### Post by klausner on 2011-01-03
> **Krytarik said:**
> It should.

Nope. Doesn't help with panel moving.

---

### Post by Krytarik on 2011-01-03
I've tested it now with exact the same setup as you have, calling the script via .profile.

Apparently the entries in .profile are executed BEFORE the desktop gets loaded, thus that cannot work.

Put the script instead in "System -> Preferences -> Startup Applications", this works.

This way you even don't have to add the extra commands, those are only necessary for crontab (and maybe other cases), I've tested both cases.

---

### Post by klausner on 2011-01-03
> **Krytarik said:**
> I've tested it now with exact the same setup as you have, calling the script via .profile.

Apparently the entries in .profile are executed BEFORE the desktop gets loaded, thus that cannot work.

Put the script instead in "System -> Preferences -> Startup Applications", this works.

This way you even don't have to add the extra commands, those are only necessary for crontab (and maybe other cases), I've tested both cases.

Curious. I also tried running the script in "System -> Preferences -> Startup Applications", and all I got was audacious to sho it had run. The panels never moved. FWIW, I'm running 10.04.

---

### Post by Krytarik on 2011-01-04
> **klausner said:**
> Curious. I also tried running the script in "System -> Preferences -> Startup Applications", and all I got was audacious to sho it had run. The panels never moved. FWIW, I'm running 10.04.
I'm also running 10.04.

Try adding the "!/bin/sh" declaration to your script:
```
#!/bin/sh
sleep 15
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation top
sleep 5
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation bottom
```

---

### Post by klausner on 2011-01-05
> **Krytarik said:**
> I'm also running 10.04.

Try adding the "!/bin/sh" declaration to your script:
```
#!/bin/sh
sleep 15
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation top
sleep 5
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation bottom
```

Turns out all the stuff with DBUS_SESSION_BUS_ADDRESS is moot for this purpose. Nor does it need to be opened in a private shell.

The key was waiting long enough for both panels to get started, So a *sleep 45* seems to do it. I'm sure there is a more elegant way to detect when both panels ar up, but this seems to work. The second *sleep 2* is needed when the script runs at startup, but not if run later.

Here's what I ended up with:
```
sleep 45

gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation top
sleep 2
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation bottom
```

---

### Post by Krytarik on 2011-01-06
That's a fairly long start-up time, did you try it before with my suggested delay time or also with 60 secs?

I just yet searched a while for a way to wait until a given process -in your case "gnome-panel"- is started before executing given commands. Unfortunately I only found a way to repeatedly check if the process is running, and if this turns out true execute the commands:
```
#!/bin/sh
until [ -n "$(pgrep -u $LOGNAME -n gnome-panel)" ];do
sleep 5
done

gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation top
sleep 2
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation bottom
```

---

### Post by klausner on 2011-01-06
> **Krytarik said:**
> That's a fairly long start-up time, did you try it before with my suggested delay time or also with 60 secs?

I just yet searched a while for a way to wait until a given process -in your case "gnome-panel"- is started before executing given commands. Unfortunately I only found a way to repeatedly check if the process is running, and if this turns out true execute the commands:
```
#!/bin/sh
until [ -n "$(pgrep -u $LOGNAME -n gnome-panel)" ];do
sleep 5
done

gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation top
sleep 2
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation bottom
```

I don't know what to say about the startup time. I tested it empirically. Could probably reduce the wait to 40 seconds, but I wanted some buffer.

That's a very cute trick for testing for the panel. Not sure it will work waiting for both, but will test. How did you search for that, and where did you find an answer? Slick shell tool!

---

### Post by klausner on 2011-01-06
> **Krytarik said:**
> ```
#!/bin/sh
until [ -n "$(pgrep -u $LOGNAME -n gnome-panel)" ];do
sleep 5
done

gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation top
sleep 2
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation bottom
```

Thinking about it, the test won't work. The "other" panel shows up ~10 seconds or more n=before the one I'm trying to move, so your test will return positive prematurely.

I'm going to try:
```
until [ -n "gconftool-2 --get /apps/panel/toplevels/top_panel_screen0/size" ];
```

and see if that works.

---

### Post by Krytarik on 2011-01-06
> **klausner said:**
> Thinking about it, the test won't work. The "other" panel shows up ~10 seconds or more n=before the one I'm trying to move, so your test will return positive prematurely.
You maybe right, one should wait another 2 secs or so after the condition becomes true, but 10 secs difference: OMG, how slow is your machine?;-) Mine is nearly 10 years old, but even then an overall wait time of 15 secs is enough.
> **klausner said:**
> 
I'm going to try:
```
until [ -n "gconftool-2 --get /apps/panel/toplevels/top_panel_screen0/size" ];
```and see if that works.
Isn't this option always the same regardless if the panel is loaded or not?

About finding the code: I have some experience with involving conditions, and the command itself I saw in a slightly different form in some threads I came over while searching, at the end I actually got this from the script I posted earlier and modified it to fit our needs.

[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

---

### Post by klausner on 2011-01-06
> **Krytarik said:**
> You maybe right, one should wait another 2 secs or so after the condition becomes true, but 10 secs difference: OMG, how slow is your machine?;-) Mine is nearly 10 years old, but even then an overall wait time of 15 secs is enough.

Isn't this option always the same regardless if the panel is loaded or not?


Well my idea for a test did NOT work. SO I need to think up another.

I don't think of my system as being especially slow (except on graphics). It a few years old, with a Core2 Duo P8600 CPU. The overall boot is, by my experience, reasonably quick, and certainly faster in the more recent Ubuntu releases.

---

