---
title: "Windows/Super/Hyper key not working with combinations"
date: 2009-08-26
forum: Desktop Environments
---

### Post by MaikoID on 2009-08-26
Hi, I'm using Ubuntu 9.04 normally with all my Compiz and applications shortcuts dependent of my Windows key. Suddenly it stop working after a normal system restart, I can't working without my shortcuts because I have two monitors and two desktops.   It works if is pressed in a "single mode", but I can't do any combination with other keys.   I looking for this issue and found a similar thread, but without solution too.  When I execute xev and press the Super key: ```
 KeyPress event, serial 32, synthetic NO, window 0x4a00001,     root 0x105, subw 0x0, time 9954037, (341,-394), root:(349,420),     state 0x10, keycode 133 (keysym 0xff20, Multi_key), same_screen YES,     XLookupString gives 0 bytes:      XmbLookupString gives 0 bytes:      XFilterEvent returns: True  KeyRelease event, serial 35, synthetic NO, window 0x4a00001,     root 0x105, subw 0x0, time 9954086, (341,-394), root:(349,420),     state 0x10, keycode 133 (keysym 0xff20, Multi_key), same_screen YES,     XLookupString gives 0 bytes:      XFilterEvent returns: False 
```  When I execute xmodmap  ```
 maiko@maiko-laptop:~$ xmodmap  xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):  shift       Shift_L (0x32),  Shift_R (0x3e) lock        Caps_Lock (0x42) control     Control_L (0x25),  Control_R (0x69) mod1        Alt_L (0x40),  Meta_L (0xcd) mod2        Num_Lock (0x4d) mod3       mod4        Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf) mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)  
```  What I can do to retrieve my Windows key function back ?

---

### Post by drs305 on 2009-08-26
Here are some things you can do to see what, if any, key assignments currently exist:

1. System, Preferences, Keyboard Shortcuts
2,
```
xmodmap -pke | grep "Super"
```

3. Open gconf-editor and look for Super key assignments (you could also assign key combos in the /apps/metacity section):
```
gconf-editor
```
Do a search for Super key assignments: Edit, Find, "Super", tick the "Search also in key values".

4. CompizConfig Settings Manager: General, Keybindings. Check for any Super/Windows key assignments.

---

### Post by MaikoID on 2009-08-26
Hi and thanks for the answer.

This is my output
```

maiko@maiko-laptop:~$ xmodmap -pke | grep "Super"
keycode 134 = Super_R NoSymbol Super_R NoSymbol Super_R
keycode 206 = NoSymbol Super_L NoSymbol Super_L NoSymbol Super_L
maiko@maiko-laptop:~$ 

```My gconf-editor and ccsm are fully of shortcuts with <Super>char.

See a screen-shot of gconf-editor in attachments.

bye.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=126306&d=1251294802[/IMG]

---

### Post by MaikoID on 2009-09-02
Help !!

---

### Post by MaikoID on 2009-09-10
I'm using my PC without any shortcuts yet, it's ridiculus T_T

I have tried 
```

sudo dpkg-reconfigure xserver-xorg

```

But did not work too.

Help!

---

