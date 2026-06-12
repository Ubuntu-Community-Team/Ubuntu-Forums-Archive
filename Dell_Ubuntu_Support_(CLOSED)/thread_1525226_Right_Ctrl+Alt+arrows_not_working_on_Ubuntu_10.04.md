---
title: "Right Ctrl+Alt+arrows not working on Ubuntu 10.04"
date: 2010-07-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by astrobob.tk on 2010-07-06
Hello,

I have just finished customizing my laptop but can't figure how to enable or solve this issue:

As you know one can navigate through different workspaces using Ctrl+Alt+arrows. This works for me for the left Ctrl+Alt but not the right ones. Could somebody help plz ?

thx

---

### Post by astrobob.tk on 2010-07-07
anyone out there ? its nothing serious but its really annoying. I am accustomed to you one hand to move between workspaces

---

### Post by astrobob.tk on 2010-07-11
still no reply ? :(

---

### Post by yaaarrrgg on 2010-07-12
My guess is that something else is trapping that key combination.   

Do you have compiz effects on?   Possibly this key combination was redefined?

Anything else running that could be listening for that key combination?

---

### Post by Penguin Guy on 2010-07-12
Try [COLOR="green"]System -> Preferences -> Keyboard Shortcuts[/COLOR] or [COLOR="Green"]System -> Preferences -> CompizConfig Settings Manager -> Rotate Cube -> Bindings -> Rotate cube[/COLOR]. Personally I have it set to *just* the arrows.

---

### Post by astrobob.tk on 2010-07-12
@[yaaarrrgg]("http://ubuntuforums.org/member.php?u=49794") & Penguin guy:

No I don't have compiz on. Actually I don't have it listed in my System>Preferences i nthe 1st place.

update: I just checked my keyboard configuration. I restored things to default & it worked out. The thing is that I have another keyboard layout which seems to have made some kind of conflict. In Ubuntu 9.04 I didnt have such a conflict. Things were going fine. How can you help in this ?

---

### Post by yaaarrrgg on 2010-07-12
The standard configuration tool can be launched on the command line like:

gnome-keybinding-properties

I would try one of two things:

1. Switch back to the new keyboard layout, launch the keyboard short cut tool (gnome-keybinding-properties), and manually set the short-cuts.  You can assign them by pressing the key combinations.  That way if the new keyboard layout is doing something funny with the key combination (translating it), it will be assigned correctly for that keyboard.  Also it should reclaim the key combination if it's been assigned more than once to two different actions.

2.  if that doesn't work, you might check the tool you are using to change the keyboard layout.  Possibly this tool has some keyboard hotkeys that it's listening for, and it's hijacked that control.

---

### Post by simosx on 2010-07-14
> **astrobob.tk said:**
> @[yaaarrrgg]("http://ubuntuforums.org/member.php?u=49794") & Penguin guy:

No I don't have compiz on. Actually I don't have it listed in my System>Preferences i nthe 1st place.

update: I just checked my keyboard configuration. I restored things to default & it worked out. The thing is that I have another keyboard layout which seems to have made some kind of conflict. In Ubuntu 9.04 I didnt have such a conflict. Things were going fine. How can you help in this ?

You need to mention which keyboard layouts you have.
Run
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

In addition, in the Keyboard Preferences, at Layouts, have a look at the 'Options...'. If you enable something from there, then it might conflict with the shortcut.

If you can provide this information, then it might be possible to figure out the problem.

---

### Post by astrobob.tk on 2010-09-15
> **simosx said:**
> You need to mention which keyboard layouts you have.
Run
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


Result:
```
layouts = [us,ara]
 options = [grp    grp:alts_toggle]
 model = 
```The "ar" layout was selected by country: Lebanon.

> In addition, in the Keyboard Preferences, at Layouts, have a look at the 'Options...'. If you enable something from there, then it might conflict with the shortcut.
Never edited the options, though i tried checking it out to see what's going on, but couldn't figure it out. Note that I just got a Dell Studio XPS, & this occurs on it as well, thoughwhen I remove the ar layout, the shortcuts return to normal contrary to the case on the current Dell Inspiron 8600 in question. Note also that the primary layout I use is the default (us) but I very rarely need to use the other "ar" layout.

> If you can provide this information, then it might be possible to figure out the problem.Hope you can help.

---

### Post by astrobob.tk on 2010-09-28
bump

---

### Post by bro brian on 2010-12-18
> **Penguin Guy said:**
> Try [COLOR=green]System -> Preferences -> Keyboard Shortcuts[/COLOR] or [COLOR=Green]System -> Preferences -> CompizConfig Settings Manager -> Rotate Cube -> Bindings -> Rotate cube[/COLOR]. Personally I have it set to *just* the arrows.
  Excellent! The [COLOR=Green]CompizConfig Settings Manager > Rotate Cube > Bindings > Rotate cube[COLOR=Black] worked for me.
  In the [COLOR=Green]Bindings[COLOR=Black], the [COLOR=Green]Rotate cube[COLOR=Black] checkbox wasn't checked.[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR] Now it all works fine. Thanks for the help, Penguin Guy! :D

---

