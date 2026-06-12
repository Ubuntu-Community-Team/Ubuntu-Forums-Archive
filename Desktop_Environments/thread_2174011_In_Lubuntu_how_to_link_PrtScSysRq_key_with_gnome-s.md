---
title: "In Lubuntu how to link PrtSc/SysRq key with gnome-screenshot"
date: 2013-09-12
forum: Desktop Environments
---

### Post by santosh83 on 2013-09-12
Hi all,

As the title says, I needed a screenshot program which a default install of Lubuntu 13.10 beta doesn't seem to have, and hence installed 'gnome-screenshot' through Synaptic.

Now I'd like gnome-screenshot to be invoked when I press the PrtSc/SysRq (PrintScreen/SystemRequest) key, as it did in previous Ubuntu version. How can I set up this hotkey under Lubuntu?

There seems to be no menu for configuring hotkeys or keyboard shortcuts in Lubuntu.

---

### Post by Rex Bouwense on 2013-09-12
You have to remember that you are talking about a beta version of Lubuntu 13.10.  It is for testing.  Every other Lubuntu version that I remember had that shortcut by default.  If the new one doesn't have it perhaps you should be saying something to the team that is developing it.
If you want to change a keybinding look here:
[http://lxlinux.com/#18](http://lxlinux.com/#18)

---

### Post by vasa1 on 2013-09-12
> **Rex Bouwense said:**
> You have to remember that you are talking about a beta version of Lubuntu 13.10.  It is for testing.  Every other Lubuntu version that I remember had that shortcut by default.  If the new one doesn't have it perhaps you should be saying something to the team that is developing it.
If you want to change a keybinding look here:
[http://lxlinux.com/#18](http://lxlinux.com/#18)
@Rex, I think OP wants to use gnome-screenshot instead.

@OP, if I understand correctly, you are correct in that Lubuntu doesn't come with a GUI for keyboard shortcuts. Instead, you need to edit ~/.config/openbox/lubuntu-rc.xml to make the changes you want. If you're planning to stay with Lubuntu (and Openbox), [http://pclosmag.com/html/Issues/201107/page08.html](http://pclosmag.com/html/Issues/201107/page08.html) is a great read. You could also look at [http://askubuntu.com/a/252282/25656](http://askubuntu.com/a/252282/25656) for how I like to use Lubuntu's default, scrot.

But, to change from `scrot` to `gnome-screenshot`, you need to open lubuntu-rc.xml and replace all mentions of `scrot` with `gnome-screenshot`.  To make the changes register without logging out and back in, run `openbox --reconfigure` from a terminal. You'll get the prompt back if you haven't messed up. Otherwise, if Openbox detects a problem, you'll get a small window giving you the line number for the error.

---

