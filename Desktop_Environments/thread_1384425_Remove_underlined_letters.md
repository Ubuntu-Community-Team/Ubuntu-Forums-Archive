---
title: "Remove underlined letters"
date: 2010-01-18
forum: Desktop Environments
---

### Post by Ubom on 2010-01-18
Does anybody know how to remove the underlining from letters on KDE (on menus and buttons for keyboard shortcuts I think)? I am currently running Kde4.4. If this can not be done through KDE would it be possible to modify the actual font itself to remove the underlining option? I never use the keyboard to navigate and with the font I am using the underlining seems to touch the letters themselves.
Also, on a side note, does anybody know what the command is to bring up the "loguout, turn off computer and restart" menu (the one that comes up when  Ctrl+alt+del) are pressed?

---

### Post by bamdad.khan on 2010-07-09
yes, i'd like to know that, too, but it seems after an hour of digging through the options, that there's no way of doing it short of recompiling something.

if somewhere _is_ an option, i'd really like to know. kde is supposed to look flashy and nice. never liked it, but it's getting there. but those menu accelerators look roadkill!

---

### Post by nerdy_kid on 2011-11-29
Any one managed to figure this out?  Really obnoxious imo, all the QT apps have underlined letters in the dialog boxes and menus :(

---

### Post by nerdy_kid on 2011-11-29
to answer my own question; as of QT 4.6.1 the QGtkStyle respects gtk-enable-mnemonics, so to disable the stupid underlined letters everywhere:

```

echo "gtk-enable-mnemonics = 0" > ~/.gtkrc-2.0 && cp ~/.gtkrc-2.0 ~/.gtkrc-3.0

```

done!

[edit]
you need to log out and back in for the changes to affect all applications.

---

### Post by pventura on 2012-08-30
This is an option in KDE.
To change this option:
[LIST=1]
[*]Open the _System Settings_ to configure _Style_
[*]Make sure you’ve selected the widget style *Oxygen*
[*]Click on _Configure…_
[*]Click on _Show Advanced Configuration Options_
[*]In the first tab (General), select an option for Keyboard accelerators visibility and select: _Show Keyboard Accelerators When Needed_ (only shown when holding down Alt)or _Always Hide Keyboard Accelerators_
[/LIST]
Click on OK

---

### Post by Toz on 2012-08-30
[ATTACH]223419[/ATTACH]
Rest in peace, old thread. 
Closed.

---

