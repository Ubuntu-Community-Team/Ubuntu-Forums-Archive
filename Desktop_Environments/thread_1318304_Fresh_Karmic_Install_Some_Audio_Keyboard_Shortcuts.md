---
title: "Fresh Karmic Install: Some Audio Keyboard Shortcuts Do Not Work"
date: 2009-11-07
forum: Desktop Environments
---

### Post by FilmAficionado on 2009-11-07
Hi,

So I did a fresh install of Karmic on my Lenovo Thinkpad T500.

Fortunately, the only issues I have are with the keyboard shortcuts...

Works:
[LIST]
[*]Volume Up = Works (OSD graphic shows)
[*]Volume Down = Works (OSD graphic shows)
[*]Mute button = Partially Works (no OSD graphic shows and does NOT UNmute)
[*]Function + F2 (Lock) = Works
[*]Function + F3 (Battery) = Works
[/LIST]

Does NOT work:
[LIST]
[*]Function + Right Arrow (XF86AudioNext does NOT work)
[*]Function + Left Arrow (XF86AudioPrev does NOT work)
[*]Function + Up Arrow (XF86AudioStop does NOT work)
[*]Function + Arrow Down (XF86AudioPlay does NOT work)
[/LIST]

I did ```
xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'

```

And the output was interesting... 

When I press the keys "a" then "b" then "c" then "d" I get the following, which seems normal:
```
keycode 38 = (keysym 0x61, a), state = 0x0
keycode 38 = (keysym 0x61, a), state = 0x0
keycode 56 = (keysym 0x62, b), state = 0x0
keycode 56 = (keysym 0x62, b), state = 0x0
keycode 54 = (keysym 0x63, c), state = 0x0
keycode 54 = (keysym 0x63, c), state = 0x0
keycode 40 = (keysym 0x64, d), state = 0x0
keycode 40 = (keysym 0x64, d), state = 0x0

```

However, when I press Function + Left Arrow (XF86AudioPrev Arrow), I get:

```
keycode 36 = (keysym 0xff0d, Return), state = 0x0
keycode 113 = (keysym 0xff51, Left), state = 0x0
keycode 151 = (keysym 0x1008ff2b, XF86WakeUp), state = 0x0
keycode 113 = (keysym 0xff51, Left), state = 0x0
keycode 151 = (keysym 0x1008ff2b, XF86WakeUp), state = 0x0

```

Any ideas?

This is what I found that look like similar problems:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281732](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281732)

Also:
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/403609](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/403609)

Notably the last comment makes sense to me, though I don't know how to implement it ("What worked for me was changing profile to Analog Surround 4.0 Output (or any other surround option) in sound preferences hardware tab.")

Any ideas? Thanks in advance guys!

---

