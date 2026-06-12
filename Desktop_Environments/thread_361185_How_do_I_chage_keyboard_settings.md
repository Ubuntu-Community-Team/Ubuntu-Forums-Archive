---
title: "How do I chage keyboard settings"
date: 2007-02-14
forum: Desktop Environments
---

### Post by mags73 on 2007-02-14
Greetings,

I have a small issue that is bugging the heck out of me.  I am trying to figure out why when I press the ~, ', `, or " key, I have to press the same key second time and will not display an ASCII character (this causes syntax errors).  Proper characters appear if I press the key once (which does not display a character, it seems to suspend the cursor) and then hit the space bar.  This is really annoying, to say the least.

Now how do I stop this, I have looked through system settings and posts.  I do have the US_EN keyboard specified properly.  I am not running Xmodmap nor do I feel that I should have to use it as this doesn't happen on my Ubuntu installed system, just in Kubuntu.

My specifications are as follows:
o Kubuntu 6.10
o Dell Latitude D510 with Standard US EN keyboard

Again, thank you in advance.  I am sure that it is a setting, I am totally lost.


-- Mags73

---

### Post by mags73 on 2007-02-14
bump

---

### Post by mags73 on 2007-02-15
Well, as it seems, I have found my own fix.  The solution was as simple as one line in my xorg.conf file.

I have read through many forums that suggest using dpkg-configure and xmodmap.  I didn't feel that I had to change my system by relying on auto-detect for devices already working, or pray that I (being quite new to Linux) may mess something up by these tools.

The bottom line is that I went through my /usr/X11/xorg.conf settings and commented out suspected keyboard settings one by one, restarting my machine with each change (of course reverting to the original settings before going on to the next).  I found that I had a setting that made my keyboard international.  

My solution to how I corrected this:

```

sudo nano /etc/X11/xorg.conf
ctrl-w (opens search option within nano - optional)
keyboard (the keyword I was looking for)

```

I modified the line in red with a comment char: #.

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        [COLOR="Red"]**#Option         "XkbVariant"    "intl"**[/COLOR] 
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

```

Rebooted with the above config and now everything is working great, no more heart-burn with something not working as expected.

As this being my first posting, I hope I have fulfilled the some type of support to this forum.  Criticism and critiques are always welcomed.

\\:D/

---

