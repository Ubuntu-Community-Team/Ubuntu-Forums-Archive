---
title: "I always get this erros message..."
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by javier.david on 2007-07-19
Why I always have to run throw the terminal this command:

[COLOR="DarkOliveGreen"]sudo compiz --replace[/COLOR]

Every time I log into my account??... And when I type the command without sudo, the effects just doesn't work!

And also I get this weird error message when I use whit sudo command (the effects works, but I can't change any configuration whit CompizConfig Setting Mananger):

[COLOR="DarkOliveGreen"]
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
Initializing zoom options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.[/COLOR]

What should I do??

Thanks!

---

### Post by brownknight on 2007-07-21
add compiz --replace to your sessions so it starts up when you boot

---

