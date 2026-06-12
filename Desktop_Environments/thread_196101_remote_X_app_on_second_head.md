---
title: "remote X app on second head"
date: 2006-06-13
forum: Desktop Environments
---

### Post by HankB on 2006-06-13
Ah... what a tangled web...

I've added a second head (an HD TV) and would like to play movies on it. My first attempt is to use it as a second X display (DISPLAY=:0.1) and use it that way. If there is a way to use it without running X, I'd be happy to try that too.

A second wrinkle is that I can't see the display from the PC that drives it. It faces the wrong way. I'd like to ssh into the box and run the player, directing output to the screen.

What I've done so far is to ssh in and run the command:

```
export DISPLAY=:0.1
gxine -f <movie file>
```

This works except that I lose keyboard access to the application. I suppose that since the keyboard is associated with the X server, it would associate with the keyboard on the system that hosts the X server and not my remote laptop.

The other problem is that the window spits out the following message every 4 seconds:

```
gnome-screensaver-Message: Failed to connect to the D-BUS daemon: Unable to determine the address of the message bus
```

I've disabled the screen saver through desktop settings, but this seems to persist. When I was  using the 'nv' (nvidia) driver, the screen on both heads flickered every time this message was produced. After upgrading to the 'nvidia' driver, the flickering has gone away. I have no idea what causes this message, but it seems to be gnome related since it does not happen when I use mplayer (but that has other problems.)

The other problem with this is that it won't work unless I log into the remote desktop. I suppose that's a permission thing with the server.

Is there a better way to resolve these issues? Eventually I would probably like to have programs running in the backtround that would drive the display so that we could watch movies regardless of who is logged on and what they are doing. That could then be driven via a web server as a remote control.

any suggestions are most welcome!

thanks,
hank

---

### Post by HankB on 2006-06-13
OK, I've done some more research and this is what I've found:

gxine has a couple ways that I can command it remotely. One is using gxine-remote and another is to read commands from stdin. Either will work for my needs.

The second issue can probably be solved by running a second X server on the other display rather than a dual headed server. I just need to figure out how to run specific applications on the other server rather than a login screen and desktop. Pointers to more information on that would be welcome.

thanks,
hank

---

### Post by mlind on 2006-06-13
I usually open media applications on my second display, which is my TV.

for example, opening vlc
```

DISPLAY=:0.1 vlc &

```

You should have keyboard and all other input methods in use only at one screen
at time while its focused. If you move your mouse pointer on other screen, apps
on first screen lose their focus.

I don't know if there's any shortcut keys, or commands to access other screen
from terminal.

Any program that supports client-server model should be easy to handle from
other screen.

---

### Post by HankB on 2006-06-13
Hi, thanks,

Problem with that is that I have to be logged in. That will annoy SWMBO if she wants to read mail or surf.

And I don't need keyboard and mouse on the other screen. I can't actually see it from the keyboard, so it's not very useful.

I've switched to running a second X server on the other display and that seems to work... except that it turns the main monitor off. (That annoys the wife too. ;) )

(I should have said I can use xine and xine-remote on the second server.)

thanks,
hank

---

### Post by mlind on 2006-06-13
[QUOTE=HankB]Hi, thanks,

Problem with that is that I have to be logged in. That will annoy SWMBO if she wants to read mail or surf.

And I don't need keyboard and mouse on the other screen. I can't actually see it from the keyboard, so it's not very useful.

I've switched to running a second X server on the other display and that seems to work... except that it turns the main monitor off. (That annoys the wife too. ;) )

(I should have said I can use xine and xine-remote on the second server.)

thanks,
hank[/QUOTE]

Running second XServer sounds like a best solution for this.
This way you both get your own playgounds and missis stays happy :mrgreen:

---

