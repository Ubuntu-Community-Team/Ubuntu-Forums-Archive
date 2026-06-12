---
title: "Keyboard issues"
date: 2005-12-26
forum: Desktop Environments
---

### Post by Brent Dax on 2005-12-26
On the first night of Hanukkah my true love gave to me a Logitech MX3000 keyboard/mouse set.  My goal for tonight (and tomorrow, I suppose) is to get it working nicely.

To that end, a few questions:
1. I have certain key combinations on my laptop (e.g. Ctrl+Up) which I want to map to X "special" keys (e.g. XF86AudioRaiseVolume) for when my new keyboard isn't connected.  I think I can do these mappings with xmodmap, but I can't figure out the right command.  How can I do it?  (If someone can give me an example of Ctrl+Up -> XF86AudioRaiseVolume along with an explanation of how to determine any "random" numbers in the command, I could probably figure out the rest myself.)
2. A lot of the keys on this keyboard are invisible--neither xev nor dmesg gives any hint they've been pressed.  These are mostly "weird" keys like the "next playlist" key, but a few (like Eject) are more pedestrian.  Any idea what I can do to fix this?
3. Additionally, there are zoom buttons on the mouse (+, -, and 100%) which are currently ineffective.  Can Ubuntu use these buttons as intended?  If not, can I put them to some other use, perhaps to switch between programs?  (There are also zoom buttons on the keyboard; the same question applies to them.)

Thanks in advance for any help.

---

### Post by Ampersand on 2005-12-26
For your first question, you can run gconf-editor (System - Preferences - configuration editor) and go to the apps - metacity folder. You can then set a key for run_command_1 to run_command_12 in global_keybindings, then set the corresponding command in keybinding_commands.

There's a bit about logitech mice here: [http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471).

---

