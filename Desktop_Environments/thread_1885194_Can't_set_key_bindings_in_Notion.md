---
title: "Can't set key bindings in Notion"
date: 2011-11-22
forum: Desktop Environments
---

### Post by x1a4 on 2011-11-22
Hi,

I'm running **Not**ion (Ion3 fork) and my key bindings don't work.  

This is the relevant portion of my ~/.notion/cfg_notion.lua: 
```

global_bindings {
  kpress(DEFAULT_MOD.."Left", nil),
  kpress(DEFAULT_MOD.."Right", nil),
  kpress("XF86AudioMute", "amixer -q -c 0 sset 'Analog Front',0 Toggle"),
  kpress("XF86AudioLowerVolume", "amixer -q -c 0 sset 'Analog Front',0 5- unmute"),
  kpress("XF86AudioRaiseVolume", "amixer -q -c 0 sset 'Analog Front',0 5+ unmute"),
  kpress("XF86Mail", "claws-mail"),
  kpress("Control+Mod1+Delete", "gnome-system-monitor"),
  kpress("XF86Search", "catfish --method=locate --path=/home/hex1a4"),
  kpress("XF86AudioNext", "exaile -n"),
  kpress("XF86AudioPrev", "exaile -p"),
  kpress("XF86AudioStop", "exaile -s"),
  kpress("XF86AudioPlay", "exaile -a"),
}

```

Is it because I use Xorg variables for the media keys?  Does Notion have its own key variables?  Neither the man page nor Notion website is of any help.  The source doesn't seem to contain key variables--at least according to find and grep.  

This is Notion v3-2011102900 installed from source without any modifications except the disabling of Xinerama. 


Thank you.

---

### Post by x1a4 on 2011-11-22
I've done some more looking and found the answer.  The ioncore.exec_on method has to be used to execute the app assigned to a key.  This following now works:
```

kpress("XF86AudioMute", "ioncore.exec_on(_, 'amixer -q -c 0 sset 'Analog Front',0 Toggle')"),

```

---

