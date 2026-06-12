---
title: "Keyboard problems"
date: 2005-04-02
forum: Desktop Environments
---

### Post by ibs on 2005-04-02
I can't change the keymap to Icelandic, i can only use the US English keymap. I always get the following error when i boot into Ubuntu:

----
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>
-------

Here are the outputs of the commands:

ibs@ubuntu:~ $ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "base", "pc101", "us", "", ""
ibs@ubuntu:~ $

ibs@ubuntu:~ $ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [is]
 model = pc101
 overrideSettings = false
 options = [grp grp:alts_toggle]
ibs@ubuntu:~ $

---

### Post by ibs on 2005-04-07
Why doesn't anyone reply?

---

### Post by providencia on 2005-05-23
I'm having the same problem.
I was just going to look into solving it tonight.
I'll let you know what I find out.

---

### Post by providencia on 2005-05-23
I was just going to look into solving it tonight.
I'll let you know what I find out.

[Edited to add my fix in case anyone finds this]

I simply went into System ->Preferences->Keyboard
Then I removed each keyboard layout.
Then, without closing I added simply US English.

In my case I couldn't get the Korean layout to work.
Each time I installed it I would get the same error.

---

