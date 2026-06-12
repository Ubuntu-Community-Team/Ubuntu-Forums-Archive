---
title: "Desktop Effects won't work in Ubuntu 7.04"
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by pavit_laul on 2007-12-08
Hi all, I just installed Ubuntu 7.04. Being a first-timer, I absolutely have no idea about Ubuntu, except maybe how to open the terminal!

Now, when I try to start the Desktop Effects, my screen goes white for about 30 seconds and then reverts back to the original one.

Any help please?

---

### Post by Ub1476 on 2007-12-08
Just so you know, Ubuntu 7.04 is the previous version of Ubuntu, 7.10 is the latest. I advice you use that instead. Anyway, have you installed your graphic driver? Also what's your graphic card?

Shows graphic card:
```
lspci | grep VGA
```

---

### Post by pavit_laul on 2007-12-08
Well yes, I was thinking of updating to it in a couple of days... But until then, I thought I'd go with 7.04. Thanks for telling.

Graphics Card :

pavit@pavit-desktop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
pavit@pavit-desktop:~$

---

### Post by Ub1476 on 2007-12-08
Check out [this guide]("http://www.ubuntu1501.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html").

> **motang said:**
> Well I was **very** happy today as I followed this [tutorial]("http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html") and got XGL working on my HP dv2000z laptop which also has ATi Radeon Xpress 200M.  Hope it works out for you.

**[COLOR="Red"]Note[/COLOR]**: But be careful and make sure that you have all your important stuff backed in case something goes wrong.

---

### Post by pavit_laul on 2007-12-09
Thanks a lot for the link. I did everything as mentioned.
But when I log-in again to the XGL session and type compiz --replace in the terminal, this is what I get : 

pavit@pavit-desktop:~$ compiz --replace
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


What to do now? :(

---

### Post by pavit_laul on 2007-12-09
I again typed compiz --replace and this is what I got : 

pavit@pavit-desktop:~$ compiz --replace
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

(gtk-window-decorator:6239): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6239): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6239): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6239): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6239): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6239): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6239): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6239): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6239): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6239): Wnck-WARNING **: Unhandled action type (nil)
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
inotify_add_watch: No such file or directory
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'keybinding'
gtk-window-decorator: Screen 0 on display ":1.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
inotify_add_watch: No such file or directory
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'keybinding'
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by Ub1476 on 2007-12-09
Post the output of

```
sudo gedit /etc/X11/xorg.conf
```

Also, try to set Visual Effects to normal, as I see the error complains about a few of the Compiz plugins.

---

### Post by pavit_laul on 2007-12-09
I updated my Ubuntu 7.04 and now everything's working, and I'm like WOW!! :)
Thanks a lot for the help...
Is there any way that I can keep the cube permanently (as in, not only when I rotate it with the mouse) ?

---

### Post by Ub1476 on 2007-12-09
You can't really work on it while you have it zoomed out, if that's what you though. Yet you can use plugins like expo, set the transparancy on the cube etc. Look around in the "Cube" plugin and "Rotate plugin", and see what pleases you most:)

---

### Post by pavit_laul on 2007-12-09
Ya, that's what I was thinking about ;)
Well, I've been looking and can't seem to get the 3D Windows thing work (I enabled it)

---

### Post by pavit_laul on 2007-12-09
One more thing, Ok, I can't work while the cube is zoomed out, but can I keep it that way, when I'm not working, without pressing/clicking any buttons.. just for the look of it ;)

---

### Post by Ub1476 on 2007-12-09
The 3d windows doesn't even come with the Gutsy (Ubuntu 7.10) v. of Compiz, so they doesn't work very well at the moment. They work for me, but causes heavy flickering. 

Not that I know of, but when pressing <Control>+<Alt>+Mouse1, you can at least stop holding down ctrl&alt.

---

### Post by pavit_laul on 2007-12-09
OK, so then, does it mean that the cube is mainly for aesthetic uses? and not of much practical use?

---

### Post by Ub1476 on 2007-12-09
Yes, probably. But workspaces (many desktops at once) is very useful. Plugins like Expo and Cube gives you a better look of where you have stored your windows though.

In my case I use the 
[LIST]
[*]Workspace-switcher
[*]Desktopwall (below desktop plane)
[*]Ekspo
[*]2 Desktop horizontal and 2 vetical (change in General settings).
[/LIST]

It takes a bit time to see the use of more desktops for most people, but for me it's a must now:)

---

### Post by pavit_laul on 2007-12-09
Also, Is it OK if I make the XGL session default instead of the current XClient Script?

---

### Post by Ub1476 on 2007-12-09
Yes, you can always change it by going into sessions anyway.

---

### Post by pavit_laul on 2007-12-12
Compiz runs fine in the XGL session...
But, everytime I give compiz --replace in the terminal at start-up, this is what I get :

> pavit@pavit-desktop:~$ compiz --replace
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (core) - Error: no 'core' plugin with ABI version '20070917' loaded

/usr/bin/compiz.real (3d) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin '3d'


Is this normal?
What does it mean couldn't activate plugin 3D? Is that why I can't get 3D windows?

---

### Post by pavit_laul on 2007-12-13
someone reply pls...

---

