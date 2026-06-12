---
title: "ZDoom/GZDoom/Zandronum/other ports hanging on keyboard"
date: 2014-10-12
forum: Gaming &amp; Leisure
---

### Post by kira-yamato-2008 on 2014-10-12
Well the long and short of it is that ZDoom and it's source ports like Zandronum and GZDoom seem to hang on the keyboard. Most people report this when hitting the T, `, and Esc key. Basically what happens as far as I understand it is that the keydown is reported, but the keyup isn't, thus making the program think that the key is still pressed down. This locks out all menu and console keyboard input, but not mouse input, and not game-play keyboard input.

Now then I've read that this isn't an issue/has been fixed with SDL 2.0, and there's also a back ported fix someone made for SDL 1.2

I would like to know either how to implement the work around, or upgrade to SDL 2.0 on Lubuntu.

---

