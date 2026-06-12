---
title: "after update to 11.04, no active titlebar!"
date: 2011-05-16
forum: Desktop Environments
---

### Post by gcbzzzz on 2011-05-16
upgrade to 11.04 (big mistake. do not do it!)

selected gnome classic.

now my title bars get all with the active color, or all without the active color. it's a crap fest

only the maximized ones work as expected.

---

### Post by wildmanne39 on 2011-05-16
> **gcbzzzz said:**
> upgrade to 11.04 (big mistake. do not do it!)

selected gnome classic.

now my title bars get all with the active color, or all without the active color. it's a crap fest

only the maximized ones work as expected.
Hi, can you be clearer on the exact problem, so we can help you.:D

---

### Post by gcbzzzz on 2011-05-16
1. open two windows (xterm, gedit, anything)
2. focus on one window (click, alt-tab, hover mouse if using focus-follow-mouse, anything)

what do you expect:
that the focused window has the "active" color on the titlebar and the not focused window has the "inactive" color.

what happens:
both windows remain with the active or inactive color. nothing changes regardless of focus changes.

workarounds:
none.

already tried:
clicking the windows.
clicking the titlebar.
alt+tabbbing from one another.

Note: the focus changes alright. i can type where i intend. the cursor blinks on the terminal i want. all is fine. just there is no window manager indication of where the focus is. i have to keep mental notes

it does work for maximized windows.
if i have a maximized window it has the 'active' color on the title bar. if i focus another window, the maximized one changes to the 'inactive' color. but all the unmaximized windows either are all with the 'active' or 'inactive' color at once (changes every boot or once in a while.). click the maximized window restore it's title bar to 'active' color. unmaximized remains as were.

---

### Post by wildmanne39 on 2011-05-16
> **gcbzzzz said:**
> 1. open two windows (xterm, gedit, anything)
2. focus on one window (click, alt-tab, hover mouse if using focus-follow-mouse, anything)

what do you expect:
that the focused window has the "active" color on the titlebar and the not focused window has the "inactive" color.

what happens:
both windows remain with the active or inactive color. nothing changes regardless of focus changes.

workarounds:
none.

already tried:
clicking the windows.
clicking the titlebar.
alt+tabbbing from one another.

Note: the focus changes alright. i can type where i intend. the cursor blinks on the terminal i want. all is fine. just there is no window manager indication of where the focus is. i have to keep mental notes

it does work for maximized windows.
if i have a maximized window it has the 'active' color on the title bar. if i focus another window, the maximized one changes to the 'inactive' color. but all the unmaximized windows either are all with the 'active' or 'inactive' color at once (changes every boot or once in a while.). click the maximized window restore it's title bar to 'active' color. unmaximized remains as were.
Hi, I agree that is strange, I will research it and see if I can find an answer,but I have not heard of this issue before.:)

---

### Post by wildmanne39 on 2011-05-16
> **gcbzzzz said:**
> 1. open two windows (xterm, gedit, anything)
2. focus on one window (click, alt-tab, hover mouse if using focus-follow-mouse, anything)

what do you expect:
that the focused window has the "active" color on the titlebar and the not focused window has the "inactive" color.

what happens:
both windows remain with the active or inactive color. nothing changes regardless of focus changes.

workarounds:
none.

already tried:
clicking the windows.
clicking the titlebar.
alt+tabbbing from one another.

Note: the focus changes alright. i can type where i intend. the cursor blinks on the terminal i want. all is fine. just there is no window manager indication of where the focus is. i have to keep mental notes

it does work for maximized windows.
if i have a maximized window it has the 'active' color on the title bar. if i focus another window, the maximized one changes to the 'inactive' color. but all the unmaximized windows either are all with the 'active' or 'inactive' color at once (changes every boot or once in a while.). click the maximized window restore it's title bar to 'active' color. unmaximized remains as were.
Hi, I just wanted to let you know I have not found a solution for your problem yet.

---

### Post by shashanksingh on 2011-05-17
> **gcbzzzz said:**
> upgrade to 11.04 (big mistake. do not do it!)

selected gnome classic.

now my title bars get all with the active color, or all without the active color. it's a crap fest

only the maximized ones work as expected.

try thi and tell us what happens.

compiz --replace

compiz-decorater --replace

Anything different??
(Im not sure if this is the solution, just curious, I have similar problems which get solved with --replace)

---

### Post by Copper Bezel on 2011-05-17
To clarify, you're using Compiz under Classic, correct? (Window decorations are drawn by either Compiz or Metacity depending on which window manager you're using, so that should narrow down the problem a bit.) I'd assume that the problem wouldn't be present under Metacity (but do try it, just in case - metacity --replace .)

I haven't seen this bug before, and I'm a little uncertain what to check at this point.

Edit: Simultaneous post. Shashanksingh, good call, but it's *compiz-decorator* . = )

---

### Post by gcbzzzz on 2011-05-18
yes, i'm using compiz with ubuntu classic.

both commands restart my windowmanager alright and what happens is that now the xterm that had the keyboard focus during the restart will have the active color on the titlebar permanently.  all other windows will be permanently inactive. ...except for the maximized ones, those are still working as before.

I tried to reset all the settings from my compiz plugins, same thing happens. also tried to disable focus-follow-mouse.

here are the compiz packages i have
```
aptitude search ~i compiz | grep compiz
i   compiz                          - OpenGL window and compositing manager     
i A compiz-core                     - OpenGL window and compositing manager     
v   compiz-core-abiversion-20110322 -                                           
p   compiz-dev                      - OpenGL window and compositing manager - de
p   compiz-fusion-bcop              - Compiz Fusion option code generator       
i   compiz-fusion-plugins-extra     - transitional dummy package.               
i   compiz-fusion-plugins-main      - transitional dummy package.               
i   compiz-gnome                    - OpenGL window and compositing manager - GN
p   compiz-kde                      - OpenGL window and compositing manager - KD
i   compiz-plugins                  - OpenGL window and compositing manager - pl
i A compiz-plugins-extra            - Collection of extra plugins from OpenCompo
i A compiz-plugins-main             - Compiz Fusion plugins - main collection   
i   compizconfig-backend-gconf      - Compiz Fusion configuration system - gconf
p   compizconfig-backend-kconfig    - KConfig Settings library for plugins - Ope
i   compizconfig-settings-manager   - Compiz configuration settings manager     
v   gcompizthemer                   -                                           
i   libcompizconfig0                - Settings library for plugins - OpenComposi
p   libcompizconfig0-dev            - Development file for plugin settings - Ope
i A python-compizconfig             - Compizconfig bindings for python          
v   python2.6-compizconfig          -                                           
v   python2.7-compizconfig          -                                           
p   utouch-compiz                   - uTouch plugin for compiz                  
```


no idea how to get the versions... but they are all up-to-date

---

### Post by gcbzzzz on 2011-05-18
it's now even weirder... works with maximized windows, gedit and synaptic.  But still is always "active" for gaim windows and xterms.

---

### Post by shashanksingh on 2011-05-18
Close all your windows,reset your compiz to defaults and then..

Alt+F2 -> compiz --replace.
Alt+F2 -> compiz-decorator --replace 
Restart

Is it still behaving wierd (as compiz does quiet often, even I'e got a problem with it)??

If you are sure you havn't installed anything else that fiddles with your window, this may be a bug.

Report it.

---

### Post by gcbzzzz on 2011-05-19
compiz --replace and a restart are paradoxal :)

edit: explaning why:
compiz --restart does not change any setting. so rebooting would just undo the transient change it caused.

---

### Post by gcbzzzz on 2011-05-19
will post a bug... metacity --replace works. so it's not a X problem.

---

### Post by drdan14 on 2011-06-08
I have the same issue.  This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/770283](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/770283)

---

