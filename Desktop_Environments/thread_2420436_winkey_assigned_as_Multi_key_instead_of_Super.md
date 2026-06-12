---
title: "winkey assigned as Multi key instead of Super"
date: 2019-06-05
forum: Desktop Environments
---

### Post by Nikos_Kyriazis on 2019-06-05
I am running xubuntu 18.04 and I have the following problem.When I try to create a shortcut using the win-key, instead of Super I get Multi Key indication and I cannot create key combination (i.e. Super-T). For example I cannot use the following shortcuts that have Super in it:

[IMG]https://i.imgur.com/zTex7I9l.png[/IMG]

there follows my /etc/default/keyboard:
```
# KEYBOARD CONFIGURATION FILE
# Consult the keyboard(5) manual page.

XKBMODEL="pc105"
XKBLAYOUT="us,gr"
XKBVARIANT=","
XKBOPTIONS="grp:alt_shift_toggle,compose:lwin,terminate:ctrl_alt_bksp,grp_led:scroll"

BACKSPACE="guess
```

also an image of Settings Editor, keyboard-layout:

[IMG]https://i.imgur.com/FkkHzdxl.png[/IMG]

Could you please help me in reassigning winkey as Super?

---

### Post by Nikos_Kyriazis on 2019-06-05
[COLOR=#1A1A1B][FONT=&amp]I'm answering my own question here in case someone finds it helpful.
[/FONT][/COLOR][COLOR=#1A1A1B][FONT=&amp]I run sudo dpkg-reconfigure keyboard-configuration and on the choice Compose key, I choose No compose key.

[IMG]https://i.imgur.com/xehnCn2l.png[/IMG][/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
I had previously chosen Left Logo key which had caused the [FONT=inherit]Super[/FONT] been substituted by [FONT=inherit]Multi Key [/FONT]when assigning shortcuts.[/FONT][/COLOR]

---

