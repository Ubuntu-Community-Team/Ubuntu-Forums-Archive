---
title: "Compiz Problem"
date: 2006-08-28
forum: Desktop Environments
---

### Post by burty89 on 2006-08-28
I have successfully installed Xgl & Compiz on my ubuntu laptop, but with a couple of problems that I wondered if anyone had encountered:

1) Window borders don't show... I have installed cgwd and a theme selection app shows up under system->preferences, however selecting a theme still doesn't show window borders

2) Visiting gmail causes X to restart, essentially it has the same effect as pressing ctrl+alt+backspace. I'm sure gmail is likely not the only thing that causes this but its the only one I've discovered so far.

I know xgl & compiz are working because I have the cube effect working, and windows 'wobble' when I move them by holding alt (only way I can move them because they have no title bar...)

This is a Compaq Presario V5120EU laptop (ATI Radeon 200m graphics) using the latest fglrx driver, although I doubt this matters as xgl & compiz are already running. The compiz files came from [http://ubuntu.systemadministrator.org/dists/dapper/eyecandy/](http://ubuntu.systemadministrator.org/dists/dapper/eyecandy/)

Other than the above issues I'm having a great time with ubuntu already, and hopefully once the above are sorted I'll have an even better one :D

---

### Post by ButteBlues on 2006-08-28
What are you using to start Compiz? Gnome-Compiz-Manager?

A script?

---

### Post by burty89 on 2006-08-28
I have a script that runs on login, can't remember exactly whats in there but its something like this:

> killall gnome-window-decorator
wait
cgwd &
compiz --replace gconf &

---

### Post by burty89 on 2006-08-28
Sorry, I just looked at the file and remembered I removed the first two lines whilst trying to get compiz to work earlier (had no effect, the problem was solved by installing compiz from the location above rather than compiz.net)

Content of the script:

> #!/bin/sh
cgwd &
compiz --replace gconf &

---

### Post by ButteBlues on 2006-08-28
#!/bin/sh
killall gnome-window-decorator
wait

cgwd &
compiz --replace gconf &


That should be working... Hmm... What driver/gfx you on?


EDIT - I'm not sure why you're asking in the AIGLX thread when your gfx is supported by fgrlx.

---

### Post by burty89 on 2006-08-28
I just tried running my script from gnome-terminal and this is what I get:

> paul@paul-laptop:~$ sudo sh /usr/bin/startcompiz
gnome-window-decorator: no process killed
paul@paul-laptop:~$ cgwd: Connection Error (No reply within specified time)
6342: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4628.
This is normally a bug in some application using the D-BUS library.
6342: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4592.
This is normally a bug in some application using the D-BUS library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...
compiz.real: No GLXFBConfig for depth 32
compiz.real: No GLXFBConfig for depth 32
compiz.real: No GLXFBConfig for depth 32
compiz.real: dbus_bus_get error: No reply within specified time
compiz.real: Plugin 'dbus':initDisplay failed
compiz.real: Couldn't activate plugin 'dbus'

paul@paul-laptop:~$


> EDIT - I'm not sure why you're asking in the AIGLX thread when your gfx is supported by fgrlx.

I'm asking in the AIGLX thread? What? This forums called desktop support and I made the thread myself, whats it got to do with AIGLX?

---

### Post by ButteBlues on 2006-08-28
Sorry - long day. I read wrong FF tab. =/

As for that, it seems like perhaps your DefaultDepth is off, and the dbus plugin is missing for some reason.

---

### Post by burty89 on 2006-08-28
In my xorg.conf, DefaultDepth is definately set to 24, and nowhere is a depth of 32 mentioned in the file, so I'm not sure why its causing a problem. One thing I do remember is that I read with fglrx xgl had to run on screen 1 instead of 0, so maybe this is causing it if the xorg.conf file is setting 24 for screen 0. (I'm grasping at straws here, I've been watching ubuntu for a while but only installed it yesterday, and haven't had much experience with linux in general)

As for dbus, any ideas about how to fix the problem?

---

### Post by ButteBlues on 2006-08-28
No ideas concerning dbus.

However, all the XGL w/ fgrlx guides I've seen should walk you through setting the display to 1 in gdm.conf.

---

### Post by burty89 on 2006-08-28
In xorg.conf I just copied the "Screen" section and changed the Identifier of the copied one to "Screen1", but this had no effect... Am I even doing this properly? I don't see why compiz should even be using depth 32.

---

### Post by burty89 on 2006-08-28
I already set display to 1 in gdm.conf-custom.

---

### Post by burty89 on 2006-08-28
Changing the script to dbus-launch cgwd & solved the dbus problem.

I found this: [http://www.compiz.net/viewtopic.php?id=1304](http://www.compiz.net/viewtopic.php?id=1304)

I just applied quinn.patch (last post) to the source of the compiz package, but had to modify screen.c myself as the patch failed for this file (the line numbers were off).

This configured, made & installed successfully, but now upon logon when compiz starts I see no windows, just a brown background and the cursor... The only way I can get anything to show is to press ctrl+alt+f1, login and run startx (so no xml/compiz)...

Anyone any ideas?

---

### Post by burty89 on 2006-08-28
Btw, running the script from gnome-terminal now gives:

> compiz: No composite extension
Couldn't load settings: Reverting to defaults.
Couldn't load theme: Reverting to defaults.

Although, I guess this is because I'm not running from within xgl, and when xgl is running compiz starts and I can't run a terminal to see whats going on, so I'm a little stuck...

---

### Post by burty89 on 2006-08-28
I removed the script from session -> startup programs so that I could run a terminal whilst xgl was running (so compiz would start), running the script now gives:

> compiz: No XKB extension and then the gnome panel & terminals title bars vanish and I can't even interact with the terminal...

---

### Post by burty89 on 2006-08-28
Of course, I just realized xkb would be the keyboard, and undid a change I made to gdm.conf-custom (addition of the -kb flag to xgl), now upon running the script I don't see the no xkb error, but other than that the result is the same (no titlebars, can't interact with terminal etc).

---

### Post by burty89 on 2006-08-28
oops, seems I actually had compiz-vanilla, not the quinn one. Maybe thats why it screwed up with the patch, am reinstalling compiz (the quinn one) now.

---

### Post by burty89 on 2006-08-28
OK, I've reinstalled compiz, I tried the patch again and the same thing happened (no panel, can't interact with terminal), so I've now reinstalled compiz yet again and am back to the problem of:

> compiz.real: No GLXFBConfig for depth 32

I definately have the quinn one now, as the effects are different to what the vanilla one used.

---

