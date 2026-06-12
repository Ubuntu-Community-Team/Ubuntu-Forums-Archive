---
title: "Monkey Bubble - no sound in Kubuntu?"
date: 2006-07-04
forum: Gaming &amp; Leisure
---

### Post by msak007 on 2006-07-04
I read about a Frozen Bubble-like game called [Monkey Bubble]("http://home.gna.org/monkeybubble/index.html") the other day and that it had the capability to play over a network, so I decided to give it a try. I found it in the repositories and it installed along with all its dependencies just fine. The game starts just fine, but there is no sound. I started it from a terminal and this is the output:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
[COLOR="Red"]/bin/sh: /usr/bin/esd: No such file or directory[/COLOR]
The value of configuration key /apps/monkey-bubble/stop_game is not valid; value is ""
The value of configuration key /apps/monkey-bubble/quit_game is not valid; value is ""
start play /usr/share/monkey-bubble/sounds/splash.ogg

** (monkey-bubble:28546): WARNING **: No GConf default audio sink key and esdsink doesn't work

(monkey-bubble:28546): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(monkey-bubble:28546): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(monkey-bubble:28546): GStreamer-CRITICAL **: gst_element_link_many: assertion `GST_IS_ELEMENT (element_2)' failed
waiting for pad
```

The developer describes it as a "gnome based bust'a'move-clone", and it seems in being Gnome based it's looking for esd for sound (highlighted in red). I'm running Kubuntu / KDE, and use aRts for sound. Is there a way to get sound working in KDE? There are no sound options in the game. I tried to compile from source and ran into numerous problems - even if I could get it to compile, there were no flags or compile options to tell it to use anything but esd for sound. There is hardly any documentation for this game so I'm not sure what to do. Anbody have any suggestions?

---

### Post by msak007 on 2006-07-09
If nobody has the answer, can anybody suggest a game like this that has network play capability?

---

