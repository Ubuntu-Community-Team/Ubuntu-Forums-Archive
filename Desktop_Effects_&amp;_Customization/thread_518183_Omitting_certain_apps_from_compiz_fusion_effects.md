---
title: "Omitting certain apps from compiz fusion effects?"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by Pixel on 2007-08-05
I've taken a liking to the motion blur effects, however, I noticed that the effects apply to any window regardless of what it is.  This include video players, I was wondering if it was possible to make them work without being affected by motion blur, or compiz all-together.

Thanks.

---

### Post by stido on 2007-08-08
i don't think controlling the blur effects (or any other effects for that matter) per application-name is possible, at least for the moment. What we can do is controlling it per window-type (normal, dialog, utility, etc.)

---

### Post by psyopper on 2007-08-08
> **stido said:**
> i don't think controlling the blur effects (or any other effects for that matter) per application-name is possible, at least for the moment. What we can do is controlling it per window-type (normal, dialog, utility, etc.)

Not quite true. [I managed to get it to ignore my Conky]("http://ubuntuforums.org/showthread.php?t=504194") by forcing it to ignore like this:

& !(class=conky | name=$conky)

Basically I added this to the end of the list of window types it effected. Unfortunately for the original question, at least in the version of CCSM I have, you cannot force blur on or off on any window. If you snoop around enough in the flatfile backend for Compiz you could probably suss out how to do it.

Unfortunately the link to the opencompositing.org forum on that thread is broken, apparently opencompositing.org is moving servers or something. The thread listed actually showed a method my which you could identify a windows properties with a terminal command that generated a crosshair. You clicked the crosshair ont he window and the terminal displayed all of the window properties.

---

### Post by psyopper on 2007-08-08
So, looking at it further you may be able to do this by editing your ~/.compizconfig/Default.ini. This is all conjecture of course, good luck in your attempt!

First you need to be running Compiz in the "flatfile" backend, not the GConf backend. TO run in flatfile open CompizConfig Settings Manager (CCSM) and click on the "Backend & Profile" button. In the Backed option choose "Flatfile Configuration" 

Warning: Changing this from GConf backend may force you to change a few of your keybindings and preferences in CCSM. It may not. Be prepared to potentially loose some of your settings and have to readjust them as necessary.

The file you want to edit is (as above) the ~/.compizconfig/Default.ini. Actually it depends if you are using the Default profile or a custom profile. Either way, open your profile in gedit (or other text editor) and poke around. I managed to get Compiz to ignore Conky as listed above. The plugins that reference particular windows all have the following line in them:

s0_window_match = ()

Except that there will be something listed in the paranthesis. Put this line in the Motion Blur[ mblur] plugin section so that it looks something like this:
```

[mblur]
s0_strength = 7.670000
s0_on_transformed_screen = true
as_____plugin_enabled = true
s0_window_match = (type=normal) & !(name=mplayer)

```

Of course this depends on how/if you can identify your video windows. Essentially the & !() is an exclusion instead of an inclusion. Of course this really depends on how the plugin was written and makes a very broad assumption that the plugins are standardized to the Compiz backend.

---

### Post by psyopper on 2007-08-08
OK, I found the tool I was talking about, it's called xprop.

In the terminal type ```
xprop
```

Your cursor will change to a crosshair. Click on the window you want to view the properties of and the terminal will display a BUNCH of stuff. For instance if I xprop a Totem Movie Player I get a bunch of gobbldeygook, and then at the end the following:

```

_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_MOVE, _NET_WM_ACTION_RESIZE, _NET_WM_ACTION_STICK, _NET_WM_ACTION_MINIMIZE, _NET_WM_ACTION_MAXIMIZE_HORZ, _NET_WM_ACTION_MAXIMIZE_VERT, _NET_WM_ACTION_FULLSCREEN, _NET_WM_ACTION_CLOSE, _NET_WM_ACTION_SHADE, _NET_WM_ACTION_CHANGE_DESKTOP, _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_NORMAL
_NET_WM_SYNC_REQUEST_COUNTER(CARDINAL) = 52428805
_NET_WM_USER_TIME(CARDINAL) = 10190818
WM_CLIENT_LEADER(WINDOW): window id # 0x3200001
_NET_WM_PID(CARDINAL) = 22796
WM_LOCALE_NAME(STRING) = "en_US.UTF-8"
WM_CLIENT_MACHINE(STRING) = "Ubuntu"
WM_NORMAL_HINTS(WM_SIZE_HINTS):
WM_PROTOCOLS(ATOM): protocols  WM_DELETE_WINDOW, WM_TAKE_FOCUS, _NET_WM_PING, _NET_WM_SYNC_REQUEST
WM_CLASS(STRING) = "totem", "Totem"
WM_ICON_NAME(STRING) = "Totem Movie Player"
_NET_WM_ICON_NAME(UTF8_STRING) = 0x54, 0x6f, 0x74, 0x65, 0x6d, 0x20, 0x4d, 0x6f, 0x76, 0x69, 0x65, 0x20, 0x50, 0x6c, 0x61, 0x79, 0x65, 0x72
WM_NAME(STRING) = "Totem Movie Player"
_NET_WM_NAME(UTF8_STRING) = 0x54, 0x6f, 0x74, 0x65, 0x6d, 0x20, 0x4d, 0x6f, 0x76, 0x69, 0x65, 0x20, 0x50, 0x6c, 0x61, 0x79, 0x65, 0x72

```

You want to key in in WM_CLASS and WM_NAME. These would be the class and name attributes I used in my example above.

---

### Post by stido on 2007-08-09
really nice stuff... i gotta try this too. thx!

---

### Post by aidanr on 2007-08-09
> **psyopper said:**
> Click on the window you want to view the properties of and the terminal will display a BUNCH of stuff. For instance if I xprop a Totem Movie Player I get a bunch of gobbldeygook

there's a nice script [here]("http://www.fh-giessen.de/fachschaft/mni/mediawiki/index.php/Beryl") that makes it a lot more friendly

---

### Post by psyopper on 2007-08-09
> **aidanr said:**
> there's a nice script [here]("http://www.fh-giessen.de/fachschaft/mni/mediawiki/index.php/Beryl") that makes it a lot more friendly

Good tip, thanks!!

---

