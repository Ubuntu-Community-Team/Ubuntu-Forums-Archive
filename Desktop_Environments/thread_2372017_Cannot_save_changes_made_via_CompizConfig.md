---
title: "Cannot save changes made via CompizConfig"
date: 2017-09-20
forum: Desktop Environments
---

### Post by lister171254 on 2017-09-20
I'm trying to change/disable the Move Window setting for the mouse; currently "<Alt>Button1". (see first attached)

Changing  this to something like "<Alt>F9" disables the setting for the mouse(second screenshot). Great, that's what I want.

When I close ccsm and reopen the original setting is restored.

---

### Post by mc4man on 2017-09-20
This is a wm preference. You can 'disable' it in very limited fashion, some wrong ways will also kill off the left button click which can be a real pita to fix.
Maybe something like this would prevent alt+button1 but not mess things up.. - 
```
dconf write /org/gnome/desktop/wm/preferences/mouse-button-modifier '"<Alt><Super>Button1"'
```
To set back
```
dconf write /org/gnome/desktop/wm/preferences/mouse-button-modifier '"<Alt>"'
```

---

### Post by lister171254 on 2017-09-20
Tried your suggestion without succsess. I assume that change should show up when I list the preferences

```
llist@LeoGamesLT:~$ dconf list /org/gnome/desktop/wm/preferences/
mouse-button-modifier
theme
llist@LeoGamesLT:~$ 

```

I also tried dconf-editor, but any change I made screwed up the behaviour of the windows without solving the problem.

ccsm seems the be the only tool that has entries for both the mouse and the keyboard to move windows, so I thought this would be the obvious place to change this.

Also, the windows can all be moved by just holding the left mouse button. No <Alt> needed. Where is that defined?
Thanks

---

### Post by mc4man on 2017-09-20
> **lister171254 said:**
> Tried your suggestion without succsess. I assume that change should show up when I list the preferences

```
llist@LeoGamesLT:~$ dconf list /org/gnome/desktop/wm/preferences/
mouse-button-modifier
theme
llist@LeoGamesLT:~$ 

```

I also tried dconf-editor, but any change I made screwed up the behaviour of the windows without solving the problem.

ccsm seems the be the only tool that has entries for both the mouse and the keyboard to move windows, so I thought this would be the obvious place to change this.

Also, the windows can all be moved by just holding the left mouse button. No <Alt> needed. Where is that defined?
Thanks

Works fine here in 16.04, what are you using?
Can also be done in cssm, the dconf command command would cause it to change or just put in there yourself. In rechecking the using of Button1 in dconf is superfluous, doesn't matter or hurt..

Attached really quick vid showing 1st changing in  terminal, the changing back followed by changing in ccsm & then checking with gsettings
(vid is small & psuedo compressed due to forum limits..

Windows moving with just l. click sounds like this got screwed up a bit. Try to restore to the default of <Alt> before anything else.

---

### Post by lister171254 on 2017-09-24
Just to clarify my questions.

[LIST=1]
[*]dconf list /org/gnome/desktop/wm/preferences/ doesn't list the change I made. I changed the (default) value from <Alt> to <Super>
[*]cssm changes don't get saved. Why not
[*]
[/LIST]

---

### Post by mc4man on 2017-09-25
> **lister171254 said:**
> Just to clarify my questions.

[LIST=1]
[*]dconf list /org/gnome/desktop/wm/preferences/ doesn't list the change I made. I changed the (default) value from <Alt> to <Super>
[*]cssm changes don't get saved. Why not
[*]
[/LIST]
Got me, super works fine as an alt replacement. Can you set all 3 windows shown to look like in screen?

---

### Post by lister171254 on 2017-09-25
While things work now, my two questions remain unanswered.

Screenshot of ccsm show now changes done via dconf-editor

---

### Post by kilaka on 2018-02-20
Having the same problem. Posted a question on SE: [https://askubuntu.com/questions/1008036/values-cannot-be-changed-in-compizconfig-system-manager](https://askubuntu.com/questions/1008036/values-cannot-be-changed-in-compizconfig-system-manager)

---

