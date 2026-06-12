---
title: "RE: Desktop issues"
date: 2008-05-18
forum: Desktop Environments
---

### Post by Aghosh993 on 2008-05-18
Hi,
Last night, I was trying to get the wallpaper plugin working in Compiz. It didn't work, so I just shutdown the system. Today, however, when I restarted it, I'm having severe problems with the desktop. Firstly, the panel doesn't load, and if it does, it's dislocated to the middle of the desktop. Also, its very tiny/hard to see. Also, everything keeps freezing up, and when I try moving a window, it leaves bits and pieces all over the screen. I think the problem is that the wallpaper plugin disabled nautilus from drawing my desktop, and now nautilus has died. Please help!!! My Ubuntu desktop is right now useless because of these problems. Can anyone tell me how to reinstall nautilus from the command line, and revert everything back to default settings?
Thanks,
Aghosh993

---

### Post by Ericwt on 2008-05-18
I have the same problem lost panel you can login gnome failsafe under options before signing in in lower left corner 
Eric

---

### Post by Tomatz on 2008-05-18
Firstly open a terminal and type (if you cant open a terminal then **alt F2** to open the run dialogue):

```
metacity --replace
```

Then disable the compiz wallpaper plugin and all other un-needed plugins and reboot.

Then post back with the outcome ;)

---

