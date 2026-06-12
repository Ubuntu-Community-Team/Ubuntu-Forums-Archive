---
title: "Keyboard layout doesn't load after reboot or re-login"
date: 2015-01-24
forum: Desktop Environments
---

### Post by spam-lin on 2015-01-24
I've been attempting to set my own keyboard variant for an aluminium MacBook with swedish keyboard. During the process I've lost something which loads the keyboard set as default ( in /etc/default/keyboard ) and I get EN-US.The thing which is different with this problem from the is that the keyboard layout map displays the correct language ( se and fi ) but the actual keys are EN-US.

[ATTACH=CONFIG]259449[/ATTACH]

I don't understand if there's some program which isn't loading, iBus and the others, or it's a mapping which has gone wrong. I've rolled back on all my changes.

My default keyboard config looks like this:

```
XKBLAYOUT="se"
XKBVARIANT="mac"
XKBMODEL="applealu_iso"
XKBOPTIONS="lv3:lalt_switch,terminate:ctrl_alt_bksp"
```

---

### Post by 7ql6 on 2015-08-02
I'm probably too late but I just ran into this issue, too.
If I am right it is a pretty old [issue]("http://askubuntu.com/questions/642082/how-can-the-keyboard-layout-in-kde-be-changed-to-apple-alu-keyboard-with-us-int").

---

