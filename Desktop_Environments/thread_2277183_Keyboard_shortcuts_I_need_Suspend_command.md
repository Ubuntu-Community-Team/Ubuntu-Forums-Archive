---
title: "Keyboard shortcuts I need Suspend command"
date: 2015-05-07
forum: Desktop Environments
---

### Post by ajgreeny on 2015-05-07
I am running Xubuntu 14.04 (with xfce-4.12 from the ppa) and having just had to get a new keyboard, I am now very much missing a Suspend key that was on the previous keyboard but is not on the new one that put the computer into suspend with no password asked.

I do not know what the command for suspend used to be with the old keyboard, and could never find out from the settings-manager dialogues, but there obviously must have been a command which that key was linked to, which is now what I am looking for.

Anyone got any ideas?

EDIT:
A second search has found a command that works for me, even though I had already spent some time looking previously.  A slightly different search-term has found it!
I have now added the command ```
dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```to the listed commands in Keyboard shortcuts and linked it to the Pause/Break key, which is otherwise unused, as far as I can make out.

---

