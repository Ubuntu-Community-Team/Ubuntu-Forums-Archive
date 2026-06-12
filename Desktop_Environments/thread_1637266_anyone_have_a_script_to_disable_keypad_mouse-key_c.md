---
title: "anyone have a script to disable keypad mouse-key control?"
date: 2010-12-04
forum: Desktop Environments
---

### Post by wamanning on 2010-12-04
i'm a staunch keypad user.  i never want to do anything with the numeric keypad except for the primary functions.  no pgup/pgdown or cursor control.  ever.

however, whenever i apply random updates to my system, the keyboard preference for Mouse Key pointer control using the keypad gets activated.   this automagic re-selection & activation of this option happens all the time without my consent.  i do not like this!

i'd appreciate any assistance, guidance or links to info which can help me with a script to disable this feature.  my plan is to run that script at boot-up so that my workstation is always good-to-go.


i'm currently running 10.04.

edit #1:  did some googling...that preference is stored in:

[INDENT][FONT="Courier New"]~/.gconf/desktop/gnome/accessibility/keyboard/%gconf.xml[/FONT][/INDENT]

and this is the data:

[INDENT][FONT="Courier New"]<entry name="mousekeys_enable" mtime="1291470749" type="bool" value="false"/>[/FONT][/INDENT]

i could use pointers on creating a script to automatically set this preference @ boot-up.

edit #2:  did more googling.  just added a line to /etc/rc.local to replace the current gconf.xml with one containing my desired settings:

[INDENT][FONT="Courier New"]cp ~/.gconf/desktop/gnome/accessibility/keyboard/%gconf.xml.bak2010dec04 ~/.gconf/desktop/gnome/accessibility/keyboard/%gconf.xml[/FONT][/INDENT]

---

### Post by wamanning on 2010-12-04
pffffft.

this doesnt work.

any help?

---

### Post by wojox on 2010-12-04
Don't you have a Num Lock key?

---

### Post by wamanning on 2011-04-08
> **wojox said:**
> Don't you have a Num Lock key?

yes.  when ubuntu updates are applied, num-lock is overridden and mousekey are re-activated.  this is something MS or Apple would do, not linux.

so when i start to use the keypad expecting to get numbers, i get nothing of the sort.

i'd like a programmatic way to disable mouse-key activation permanently or at boot-up.

---

### Post by grahammechanical on 2011-04-08
This kept happening to me. It is annoying. Have you tried going to System>Preferences>Keyboard? Select the mouse keys tab and untick the box called Pointer can be controlled using the keypad. I had to do this every time it happened and then for some reason it stopped happening. And I have not had this problem for weeks.

Regards.

---

### Post by stinkeye on 2011-04-08
Don't see why this is happening but the terminal command to
turn mouse keys off is...
```
gconftool-2 --set /desktop/gnome/accessibility/keyboard/mousekeys_enable --type bool false
```


and the command to add to startup applications
```
bash -c 'gconftool-2 --set /desktop/gnome/accessibility/keyboard/mousekeys_enable --type bool false'
```

---

