---
title: "Problem with switching monitors"
date: 2010-01-21
forum: Desktop Environments
---

### Post by fmouse on 2010-01-21
I'm running Ubuntu 8.04.3 LTS on my Dell (Latitude D600) laptop and it works well.  The screen resolution on the laptop's screen is 1024 x 768.  On occasion, I connect the video and audio to a flat panel LCD TV with a resolution of 1920 x 1080.  If I boot the laptop with the connection to the TV in place, I can switch the display to the higher resolution, however only a portion of the display's functionality makes the jump.  My desktop's wallpaper goes full screen on the TV, and I can move the pointer anywhere on this display, I can likewise drag any open window into the larger area, and if I do this, and the window is partially outside the smaller display area, then the window maximizes to fill the TV screen.

On the other hand, my Gnome panels remain justified to a 1024 x 768 area in the upper left of the larger display, including a panel on the right which pretty much runs down the right middle of the larger viewing area.  If I maximize a window which is contained entirely within the 1024 x 768 area, it only expands to fill this area, not the entire 1920 x 1080 area.

Additionally, if I'm watching a streaming video and press the button to expand it to full screen mode, it only occupies the smaller viewing area, and generally not even all of that, so it's actually _smaller_ than it is without the TV connected.

There appear to be at least two, maybe more, locations in the system where the current display size is registered.  xdpyinfo correctly reports the larger resolution, so the X server is apparently seeing the larger display space, but this isn't being propagated into gnome, nor into whatever mechanism determines the full screen mode display area.

I'd like to be able to switch the display _fully_ to the larger monitor size, and in particular I'd like to be able to display streaming video full-screen, or close thereto.  The best solution I have so far is to boot the system _without_ the TV connected, log in, and then connect the TV and use the Fn-CRT/LCD key combo to turn on the external VGA output.  The TV sees its input as 1024 x 768 and sizes its picture accordingly, which ends up being vertically correct (full height), but horizontally challenged.  This is acceptable for streaming video, but little better than the laptop's own monitor for other purposes.

I'd appreciate any insight on how to manipulate the effective screen size for all these contexts.

---

