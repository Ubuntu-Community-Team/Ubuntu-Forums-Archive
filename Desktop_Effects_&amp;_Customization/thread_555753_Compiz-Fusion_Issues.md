---
title: "Compiz-Fusion Issues"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by markclewis1 on 2007-09-20
I did an update of Compiz-Fusion to latest version a few days ago and completely lost the compiz desktop environment (don't know why).

In terminal, I did a compiz --replace, and that brought compiz back but only kind of, now instead of having a cube, I have 2 panes that flip like a rotating door.  I checked the settings in compiz manager and all of my settings are still the same (set-up for rotating cube, panes, etc.).

When I did the compiz --replace, I got this error message:

/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


Any suggestions or ideas?

M

---

