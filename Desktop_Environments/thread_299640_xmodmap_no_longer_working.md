---
title: "xmodmap no longer working"
date: 2006-11-14
forum: Desktop Environments
---

### Post by justinlindh on 2006-11-14
I've been using xmodmap to remap my Caps-Lock to Escape, and this has always worked as expected until about a week ago. Could a recent update have broken this, or am I doing something wrong?

My xmodmap output before running my script:
shift       Shift_L (0x31),  Shift_R (0x3d)
lock        Caps_Lock (0x41)
control     Control_L (0x24),  Control_R (0x5e)
mod1        Alt_L (0x3f),  Alt_R (0x60)
mod2      
mod3        Num_Lock (0x61)
mod4      
mod5 

My script:
!
! Swap Caps_Lock and Esc
!
remove Lock = Caps_Lock
keysym Caps_Lock = Escape
keysym Escape = Caps_Lock
add Lock = Caps_Lock

Output after running above script:
shift       Shift_L (0x31),  Shift_R (0x3d)
lock        Caps_Lock (0x41)
control     Control_L (0x24),  Control_R (0x5e)
mod1        Alt_L (0x3f),  Alt_R (0x60)
mod2      
mod3        Num_Lock (0x61)
mod4      
mod5 

As you can see, the output is the same. Any idea why this is no longer working for me, or of an alternative way to re-map my caps lock to escape? I'm a Vi guy and am going nuts without this mapping. Thanks in advance :)

---

