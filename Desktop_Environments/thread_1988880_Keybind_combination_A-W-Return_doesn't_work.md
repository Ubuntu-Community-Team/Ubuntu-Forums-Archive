---
title: "Keybind combination A-W-Return doesn't work"
date: 2012-05-28
forum: Desktop Environments
---

### Post by schifazl on 2012-05-28
Hello!

I've just replaced Ubuntu with Lubuntu on my file server/HTPC and I have some troubles in configuring a specific keybind in the lubuntu-rc.xml file. My remote sends the specified key combination (verified with xev) and I would like to use it to launch XBMC.
I've tried:
```
A-W-Return
W-A-Return
Alt_L-Super_L-Return
Super_L-Alt_L-Return
```

The complete XML section of my last try:
```
    <keybind key="A-W-Return">
        <action name="Execute">
            <command>xbmc</command>
        </action>
    </keybind>
```

But no one works. I've tried to bind A-F4, just to test, and this combination works.
What am I doing wrong?
Thanks :)

---

