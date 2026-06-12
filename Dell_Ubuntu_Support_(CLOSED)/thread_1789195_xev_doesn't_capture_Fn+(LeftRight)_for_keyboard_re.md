---
title: "xev doesn't capture Fn+(Left/Right) for keyboard remapping\."
date: 2011-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Bubble32 on 2011-06-23
Hey there!
I'm running on Inspiron 1564 and willing to remap my keyboard to have Fn+Left mapped to Home and Fn+Right to End -as in Macbooks.
I already know I should use:
```
 xmodmap -e keycode ### = Home/End 
```
and tried xev to figure out the keycode for Fn+Right and Fn+Left but to no avail. It's like xev doesn't feel a thing when I press the combination! I did, however, doubt that maybe xev doesn't capture key combinations...(?)
Any ideas how to get the keycodes for them -or maybe assign them if not already assigned?!
Thanks a lot! :)\.

---

