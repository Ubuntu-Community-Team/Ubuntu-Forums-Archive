---
title: "Compiz Fusion + Emerald Error"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by ineedaname on 2007-09-13
Hello. I'm an Ubuntu n00b. I'm currently running off of an install I did with Wubi.
So far I absolutely love Ubuntu. I'm just trying to get used to the various differences in using Ubuntu in comparison to my previous Windows installation.

Of course, the first thing I've started after installing Ubuntu is getting a compositing manager running (Compiz Fusion in this case.)

I have a bit of a problem though. Everything runs fine. I've got Avant Window Navigator, Compiz Fusion, and Emerald all running - yet Compiz Fusion and Emerald seem to have some issues that need to be worked out.

Since this is my first day in Ubuntu, and I have no idea as to what I'm doing; I have no other way to explain what my problem is, so I'll just give the brief terminal logs detailing the problem.

Compiz Fusion: (Currently it just runs as a default install - no options I enable work)
```

root@ubuntu:/home/mike# compiz --replace -c emerald &
[1] 9114
root@ubuntu:/home/mike# /usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
root@ubuntu:/home/mike# Reloading...

```

Emerald: (This now runs under the default theme - even though others are installed, and I am selecting them, no change is made. Here is what I get:)
```

root@ubuntu:/home/mike# emerald --replace

(emerald:10099): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10099): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10099): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10099): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10099): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10099): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10099): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10099): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10099): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10099): Wnck-WARNING **: Unhandled action type (nil)

```
NOTE: This continues for some time after running emerald. When changing theme, this is what is shown:
```

Reloading...
Reloading...
Reloading...
Reloading...

```

If you can provide any insight as to what the root of the problem may be - please go into detail. I'm just trying to get my feet wet in this. Thank you.

---

### Post by Forlong on 2007-09-13
Why in gods name are you running Compiz as root? o.O

And how did you install Compiz Fusion, this doesn't look right - but this could be due to the fact that your using a root-Terminal...

---

### Post by ineedaname on 2007-09-13
[http://ubuntuforums.org/showthread.php?p=3255930#post3255930](http://ubuntuforums.org/showthread.php?p=3255930#post3255930)

That'd be it. I also have AWN installed. It works perfectly.
What effect would running in the root-terminal have? Again. I'm a n00b.
I just thought that this was a substitute to sudo. I did install it in the root-terminal. Yet would that have any difference?

What is your best guess?

Also.
When I added compiz --replace -c emerald & into the startup, it works with all of the enabled plugins; then crashes after a minute or so back into metacity. It also crashes when I try using the cube. Everything else works though.

---

### Post by Islington on 2007-09-13
hopefully this is not just the blind leading the blind, but have you tried just [compiz --replace ]?

---

