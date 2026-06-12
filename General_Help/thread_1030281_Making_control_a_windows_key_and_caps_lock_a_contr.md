---
title: "Making control a windows key and caps lock a control key with xmodmap."
date: 2009-01-04
forum: General Help
---

### Post by h4ck3r on 2009-01-04
Hey guys, I have a slight problem, I am very close to having solved it, but need just that little nudge to get this working just right.

I want to switch my control key to the caps lock key, but then I want to make the old control key into a windows key. Here is my "~/.Xmodmap" file:

```
! Removing Caps_Lock from it's binding in the Caps Lock key section.
remove Lock = Caps_Lock
! Removing the left Control from the Control key section.
remove control = Control_L
! Remapping caps lock as the right Control, not yet added to the Control section yet though.
keysym Caps_Lock = Control_R
! Remapping the left Control key as the left Super key (left windows key)
keysym Control_L = Super_L
! Adding the right Control back into the control section now mapped to the Caps Lock key.
add control = Control_R
! Adding the left Control key, which is now mapped as a super key, into the super key section.
add mod4 = Control_L
```

I put the comments in as my way of trying to explain what I am doing, but, it isn't working exactly right. Here is what "xmodmap" gives me:

```
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock
control     Control_R (0x42),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  XF86LaunchC (0xcd)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
```

I think that I need to have Control_L in the mod4 section, and I need to have Control_R in the lock section (This is just what I think though, I don't really know for sure). Both control and the "windows" key are working right now, but the control key gives me a beep most of the time whenever I use it, so I don't think it is exactly right. So basically, it is working right now like I want it, but the beep that the control key gives off whenever I use it has me thinking I don't have it exactly right, and xomdmap doesn't give me the output I think it should...

Any tips would be greatly appreciated.
Thanks!
Benjamin

---

### Post by h4ck3r on 2009-01-04
benjamin@elf:~$ bump
-bash: bump: command not found
benjamin@elf:~$

---

