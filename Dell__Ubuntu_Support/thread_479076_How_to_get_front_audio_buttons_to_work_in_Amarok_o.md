---
title: "How to get front audio buttons to work in Amarok on Dell Inspiron"
date: 2007-06-19
forum: Dell  Ubuntu Support
---

### Post by kidcharles on 2007-06-19
Okay, I've tried to set up Amarok (under Settings->Configure Global Shortcuts) to use the media buttons on the front of my Inspiron E1505n to no avail. The buttons show up as "XF86AudioPause" and similar when I press them during configuration, but they don't actually do anything. Anyone have any luck with this or have any ideas? Thanks.

---

### Post by haiku99 on 2007-06-20
I posted something on geting USB speaker buttons to work that might be helpful at 
[http://ubuntuforums.org/showthread.php?t=254474](http://ubuntuforums.org/showthread.php?t=254474)
edit-
or actually the post I have a link to probably would be better for your situation...

[http://ubuntuforums.org/showthread.php?t=237408](http://ubuntuforums.org/showthread.php?t=237408)

---

### Post by kidcharles on 2007-06-21
Thanks for the links, I'll have to sit down and try to get it to work.

---

### Post by neptho on 2007-06-21
This is easiest to automate with xbindkeys.  I've set mine up for use with audacious:

```
%cat .xbindkeysrc 
"audacious --play-pause"
  m:0x0 + c:162 
  XF86AudioPlay 
"audacious --stop" 
  m:0x0 + c:164 
  XF86AudioStop 
"audacious --rew" 
  m:0x0 + c:144 
  XF86AudioPrev 
"audacious --fwd" 
  m:0x0 + c:153 
  XF86AudioNext
```

---

### Post by Tethtibis on 2007-06-27
unfortunately, you'll have to find a way to install the native windows chip set drivers, or a Linux facsimile.

---

