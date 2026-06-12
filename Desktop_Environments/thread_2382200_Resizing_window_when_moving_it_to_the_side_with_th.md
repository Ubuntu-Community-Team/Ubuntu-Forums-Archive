---
title: "Resizing window when moving it to the side with the mouse"
date: 2018-01-10
forum: Desktop Environments
---

### Post by johnmne on 2018-01-10
Similar in "Windows 10" - when you drag a window to the left/right side of the screen, the window should be resized so that it fits to the left/right side of the screen (50%).
I don't even know how it's called..

How do you do that?

I think it was enabled once and somehow got disabled..

Using Ubuntu 16.04 LTS.

---

### Post by TheFu on 2018-01-10
I'm not certain, but google found this: [http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux)

---

### Post by again? on 2018-01-10
You should be able to re-enable window snapping in the window manager section of unity-tweak-tool.
May have to install unity-tweak-tool.
[[img]https://cdn.scrot.moe/images/2018/01/10/119.md.jpg[/img]](https://scrot.moe/image/6CiJL)

---

### Post by johnmne on 2018-01-11
Thanks guys.

I see in CCSM that "Snapping Windows" (under Window Management) is enabled.
But still I can't get windows to snap.

Also I noticed that a guest user can snap windows.

I assume that 'unity-tweak-tool' isn't different than CCSM in this regard so it won't do any better..

---

Edit:

I enabled the plugin "Grid" in CCSM and now it works !! 

Thank you.

---

### Post by again? on 2018-01-11
Edit: Fixed
[s]You could reset compiz.
```
dconf reset -f /org/compiz/
Log out.
```[/s]

---

### Post by TheFu on 2018-01-11
If the solution is working, please mark the thread as "solved".  That helps the community, so people looking for a solution see it and people looking to help don't waste their time.

Thanks for saying the "grid" was needed. THAT will really help others.

---

