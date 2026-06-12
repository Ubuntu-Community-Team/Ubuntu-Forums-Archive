---
title: "Change keyboard language"
date: 2010-06-13
forum: Desktop Environments
---

### Post by qwasqwas on 2010-06-13
Hi, I wonder, is there some way to change keyboard language to specific language by hotkey?
For example:
Shift+Alt+1 - English
Shift+Alt+2 - Russian
Shift+Alt+3 - Ukrainian

---

### Post by simosx on 2010-06-14
> **qwasqwas said:**
> Hi, I wonder, is there some way to change keyboard language to specific language by hotkey?
For example:
Shift+Alt+1 - English
Shift+Alt+2 - Russian
Shift+Alt+3 - Ukrainian

You could use Keyboard Shortcuts (in Preferences), where you set Ubuntu to execute commands when you press those shortcuts.

You can assign to run the command 'setxkbmap us' for English, 'setxkbmap ru' for Russian and I think 'setxkbmap uk' for Ukrainian.

Please report back if this worked for you :-)

---

### Post by qwasqwas on 2010-06-14
> **simosx said:**
> You could use Keyboard Shortcuts (in Preferences), where you set Ubuntu to execute commands when you press those shortcuts.

You can assign to run the command 'setxkbmap us' for English, 'setxkbmap ru' for Russian and I think 'setxkbmap uk' for Ukrainian.

Please report back if this worked for you :-)

Thanks a lot, it helped me.
However, System -> Preferences -> Keyboard Shortcuts seems a bit buggy(it doesn't work correctly with Shift+numbers hotkeys), but I managed to do what I wanted by editing "apps/metacity/keybinding_commands" in gconf-editor.
Also it seems that setxkbmap resets list of available keyboard languages, but, as for me, this is not a big problem.

---

