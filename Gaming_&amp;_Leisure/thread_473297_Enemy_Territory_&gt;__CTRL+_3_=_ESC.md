---
title: "Enemy Territory &gt;  CTRL+ 3 = ESC ??"
date: 2007-06-13
forum: Gaming &amp; Leisure
---

### Post by ABCC on 2007-06-13
Ever since I made the permanent switch to linux I've been having to cope with an odd quirk in ET. When I'm a medic or fldops I frequently heal or reload myself while crouching in cover, depressing 'CTRL' for the duration. When I switch to my main weapon by hitting '3' I am always presented with the pause menu rather than my weapon of war. This naturally occurs most often on inopportune moments, resulting in loss of life or a missed opportunity to gun someone down. This feature has been persistent across distros; Gentoo, Arch and every Debian based distro I've used behaved the same way.

So, my question is this: Why does 'CTRL + 3' generate an 'ESC' (or other sequence that will pause the game) and is there a solution to this?

My life is, quite literally, at stake here. I depend on you all to ease my woes!


Regards,

ABCC

---

### Post by Cappy on 2007-06-14
Try going to (System-->Preferences-->Windows) and changing the "movement key" to Super.

---

### Post by ABCC on 2007-06-14
That didn't work. First off, window movement defaults to 'ALT' not 'CTRL' and second, that ought to be disabled in fullscreen mode.  Anyway, Ive tested it to no avail, the exact same thing still happens. I've rechecked my et settings, even with a default one this seems to happen. I would be surprised to find out I'm the only one that has this.

---

### Post by przemq on 2008-03-27
I've found semi-solution for this problem. The issue is in Xserver, because this happens (CTRL+3 = ESC) also in other X - applications. Just check what events window in X receives  **$ xev**. I haven't found where these shortcuts are bound to edit them, but there is a way to temporary disable them.

this is my etpro - start script:

```
#!/bin/bash
export LIBGL_DEBUG=verbose
xmodmap -e "remove Control = Control_L"
et +set fs_game etpro "$@"
xmodmap -e "add Control = Control_L"

```

After removing Control_L and maybe other keys from modifier maps the shortcuts with these keys will stop working. So you will be unable to use ex. Ctrl+C in terminal, etc... But in game these combinations are not used. Just remember not to have binds with CTRL in Teamspeak, or ETswitch. After closing game started with this script, everything goes back to normal. 

In previous version i've been also removing Alt_L and Control_R but i realized that it didn't helped me at all. Now its ok, I can use ctrl+3, ctrl+alt, and it works good, and its more safer because there is still ctrl+alt+F1, f2 etc. combination available through Right Control.

---

### Post by storn on 2008-04-27
hello dear ubuntu users,

this is the only thread about "CTRL + 3" problem
I'm an Enemy territory Gamer. While playing I use "CTRL + 3" combination a lot because under "3" I have my smg. It's a pain in the *** when I press this combination and "menu" of the game pops up... the game stops for me, I cannot move unles I press ESC to leave "menu".
I'm totally new to ubuntu and linux stuff. If there is any easy explanation [step by step] for me I'd be more than grateful !

thanks in advance

---

