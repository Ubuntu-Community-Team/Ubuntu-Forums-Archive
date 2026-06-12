---
title: "Funny Screen Resolution"
date: 2008-12-05
forum: General Help
---

### Post by Chuchaqui on 2008-12-05
I was trying to play a game under wine (Call of Duty 4). It didn't work and the game ended up crashing, like is usually does. Sometimes when this happens, the screen resolution and font settings are changed by the game, which is a bother since I have to hit ctrl+alt+backspace, log back in, and open all of the programs again... This time, however, I decided that I would try to change it back without logging out. So I went to screen resolution and changed it to the smallest size. That didn't quite do it so I changed it back and hit ctrl+alt+backspace and logged in again. When I did that this time it didn't effect the screen size. So I went into screen resolution and changed it to the largest size possible.

Now it looks like my old screen but there are weird problems. It's like my computer thinks it's screen is smaller then it actually is.

For example, when I typed my name in to login to ubuntuforums, a dropdown menu appeared, as it usually does, with my user name; but instead of the box appearing below the box I typed  it in, it appeared in the middle of the firefox screen, like it thought the screen was smaller then it actually is. It does this for random things too.

Is there any way to fix this?

---

### Post by ajmorris on 2008-12-06
hi there,
instead of setting it via the GUI screen resolution tools, it may be beneficial to set it via xrandr instead. So open up a terminal, and enter in the following(example using a 1280 X 1024 resolution, change it to whatever you want):
```
sudo xrandr -s 1280x1024
```

That will set your resolution. And hopefully avoid the issue you're having... that coincidentally, i have only ever seen before in windows...


AJ

---

