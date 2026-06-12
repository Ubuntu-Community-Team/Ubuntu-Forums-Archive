---
title: "Gnome wmctrl and window size"
date: 2020-04-28
forum: Desktop Environments
---

### Post by yaminb on 2020-04-28
Question:
How are the coordinates as a result of wmctrl -lG calculated
example: 0x04c0000a  0 2386 1018 682  503  abcd defg

The 2386 is the x-offset as far as I know.
The monitor it is on is 1920x1080 (confirmed in Settings-Screen Display)

I do have a dual monitor setup, but all windows are on the first display.
So how can the x-offset (2386) be greater than 1920?

How do I find the 'max x-offset' of the first display?

Background:
I'm writing a simple script to move any windows on the 2nd monitor to the 1st monitor.
I'm doing this to resolve an issue where if the 2nd monitor is off, the application will sometimes open on that off monitor and I have to work to bring it back to the first.

---

### Post by yaminb on 2020-04-28
Hmm this is weird. It looks like 1920 is the max as expected for most windows.
But there is this rogue terminal window, that gets these large x-offset values? It responds properly as in I move it left, the value decreases... but it's still a large number)

Very strange.

---

