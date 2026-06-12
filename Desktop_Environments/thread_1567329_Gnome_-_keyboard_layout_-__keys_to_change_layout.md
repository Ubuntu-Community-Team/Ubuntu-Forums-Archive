---
title: "Gnome - keyboard layout -  keys to change layout"
date: 2010-09-03
forum: Desktop Environments
---

### Post by a271828 on 2010-09-03
I am using several keyboard layouts. The most comfortable keys for me to do switch are:
Shift+Alt+1
Shift+Alt+2
Shift+Alt+3
...
How do I configure this?
Thank you.

---

### Post by Silent Warrior on 2010-09-03
Go to your Keyboard settings. If you already have a layout indicator in your systray/notification area, right-click that one and go to Settings. In the Layout-tab, click the button labelled Options... You should have a window pop up that you can scroll down. Look for 'Key(s) to change layout' - Alt+Shift is listed. Don't ask me what else might need tweaking, though...

---

### Post by a271828 on 2010-09-03
Thank you "Silent Warrior" -- but I know this -- there is not way to get what I need there.

I was able to create "short-cuts" for
Ctlr+Alt+1 and have it run "setxkbmap us"
...
Ctlr+Alt+3 and have it run "setxkbmap ro"

But this does not really work -- not sure why -- may be because of recent Ubuntu update?
Any ideas?

---

### Post by a271828 on 2010-09-25
With above approach there is another problem -- it applies new layout to all windows, but I need it for the active window ONLY.

Anybody any ideas?

---

### Post by Silent Warrior on 2010-09-26
I think the graphical utility - the layout-switcher - can be set to that behaviour. From what you say, though, it doesn't seem like it behaves quite like what you're asking for with regards to hotkeys...

---

### Post by GrouchyGaijin on 2010-10-26
> **a271828 said:**
> Thank you "Silent Warrior" -- but I know this -- there is not way to get what I need there.

I was able to create "short-cuts" for
Ctlr+Alt+1 and have it run "setxkbmap us"
...
Ctlr+Alt+3 and have it run "setxkbmap ro"

But this does not really work -- not sure why -- may be because of recent Ubuntu update?
Any ideas?

I'd like to do the same thing but with setxkbmap se and setxkbmap us.

---

### Post by a271828 on 2010-10-26
Recently I tried KDE (before I tried Gnome). KDE has exactly the same combinations of keys listed for keyboard layout-switch.

If I try to any custom action for 
Shift+Alt+1
Shift+Alt+2
Shift+Alt+3

it does not work (both KDE and Gnome).
Probably the issue lays deeper in X.
Are there any X experts who can explain if there is a way to make those shortcuts working?

---

### Post by avi9526 on 2011-04-15
For those people who maybe interesting this now (like me) I find a way to do what described in 1st post using program gxneur, its allow to define individual hotkey for some layout. But, its not works in gksu window and now i have problem with this program in 10.10. So, maybe someone have better ideas?
Really need to get working:
Ctrl+Shift+1 - EN
Ctrl+Shift+2 - RU
Ctrl+Shift+3 - UA

---

### Post by a271828 on 2011-12-11
15 months later the problem is not solved yet.
I am using: "setxkbmap ro" mapped to "Ctlr+Alt+3". Other then inconvenience of "Ctrl+Alt" "ro"-layout applies to all windows. Where is flexibility of Gnome?

---

