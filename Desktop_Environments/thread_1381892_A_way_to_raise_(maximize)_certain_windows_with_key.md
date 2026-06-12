---
title: "A way to raise (maximize) certain windows with keyboard shortcuts"
date: 2010-01-15
forum: Desktop Environments
---

### Post by zmktmk on 2010-01-15
Hi,

I'm looking for a way to raise (maximize) a window running some certain application (eg. firefox) with a gnome keyboard shortcut.
I know that some window managers (eg. xmonad) have the possibility to bind a "run or raise" action to a key, that raises a window with an app when it hasn't been launched, or launches it otherwise.
If you know any feature, tool that I could make use of, please help.

TIA,
Tomek

---

### Post by hariks0 on 2010-01-15
Hope you can use an icon in a dock for that.

---

### Post by stinkeye on 2010-01-15
> **zmktmk said:**
> Hi,

I'm looking for a way to raise (maximize) a window running some certain application (eg. firefox) with a gnome keyboard shortcut.
I know that some window managers (eg. xmonad) have the possibility to bind a "run or raise" action to a key, that raises a window with an app when it hasn't been launched, or launches it otherwise.
If you know any feature, tool that I could make use of, please help.

TIA,
Tomek
wmctrl allows you to do various window manager actions from the command line. A useful feature is "wmctrl -a <str>", which will switch to a window containing the string <str> in the title. For example, to activate a firefox window, and start firefox if there is no such window, use the following command: 
```
wmctrl -a Firefox || firefox
```

---

### Post by zmktmk on 2010-01-19
> **stinkeye said:**
>  
```
wmctrl -a Firefox || firefox
```

This is exactly what I've been looking for. Thanks a lot.

---

### Post by fbicknel on 2011-03-25
Ok, folks... here's an interesting dilemma:

This solution worked perfectly one day, but now I have to wrap the command line in sh -c '...' to get it to work.

What changed, I wonder?

Here's what changed:

[LIST]
[*]Upgraded this morning (snip from log attached)
[/LIST]
Admittedly there might be a better thread for this, but I couldn't find one.  It's more menu related than wmctrl, I would assume.

---

