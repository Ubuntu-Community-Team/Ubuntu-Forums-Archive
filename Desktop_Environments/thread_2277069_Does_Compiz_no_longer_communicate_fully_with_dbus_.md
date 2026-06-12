---
title: "Does Compiz no longer communicate fully with dbus? Passing commands"
date: 2015-05-06
forum: Desktop Environments
---

### Post by Copper Bezel on 2015-05-06
I'm attempting some light tweaking and trying to replace some workarounds I have with Touchégg that presently use xdotool to spoof keyboard input to trigger events in the Unity / Compiz shell. The arrangement emulates OSX trackpad gestures for desktop switching, etc. I'm attempting to follow the instructions provided in the Compiz wiki on the [dbus page]("http://wiki.compiz.org/Plugins/Dbus"). Every command I pass has one of three outcomes, though - the command or interface isn't recognized, or the message is sent with no result or terminal output, or the desktop crashes to the login screen. 

Partly, I'd just like to use this to replace my somewhat unreliable xdotool hacks, but I'd really like to use the example from the wiki of invoking the switcher to shift to the next window (as explained on the wiki, subsequent invocations would pass to subsequent windows, not cycle back and forth between two) and bind it to a particular trackpad gesture. Touchégg can execute commands, including dbus send, so the trackpad is irrelevant - I'm just trying to figure out if the Compiz dbus interface is still usable, and if so, how.

Since Compiz is now maintained fully through Ayatana and Unity (correct?), I understand if the Compiz wiki is out of date, but does this dbus interface still work at all, and if so, what am I doing wrong?

---

### Post by kostkon on 2015-05-06
You probably need to enable the plugin for dbus first (?), using CCSM for example, and then you can use an app like [d-feet]("https://apps.ubuntu.com/cat/applications/d-feet/") to easily test and debug your dbus calls before putting them down as actual dbus-send commands in your script.

---

### Post by Copper Bezel on 2015-05-06
I did enable the plugin, else I wouldn't have been able to crash the desktop calling it, but I looked briefly and didn't find anything to do this kind of testing with d-bus, so thank you very much for recommending d-feet!

Edit: Hmm. Get (and presumably set and list) work, but the "allscreens" interfaces that include "activate" aren't listed in D-Feet. Dbus doesn't kick my commands back as it would if the interface wasn't there, though, either. Going to take further futzing.

Edit: dbus is not as simple to pass commands to as I'd thought. I'm going to need to learn the syntax and look for documentation for specific options. It doesn't seem to be any problem with Compiz at all, so I'm marking the thread Solved.

---

