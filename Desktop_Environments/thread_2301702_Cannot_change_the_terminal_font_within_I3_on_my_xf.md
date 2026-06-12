---
title: "Cannot change the terminal font within I3 on my xfce ubuntu 14.04 lts enviroment"
date: 2015-11-04
forum: Desktop Environments
---

### Post by gmercer015 on 2015-11-04
I just recently installed I3-gaps and it's working great, minus the fact that I can't seem to change my terminal font. I know from reading online the terminal depends on gtk settings, so I went ahead and downloaded *lxappearance *. When I start is up I initially get the error

```
(lxappearance:4251): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
```

which will appear about 8 times with the same message. Other than that lxappearance starts up fine. The problem is that none of my settings are saved if I try to modify the font and i3-msg restart / reload or log out and in. the app will modify my .gtkrc-2.0 correctly, but no changes are actually made to the applications. 

Here's what I've already tried:
[LIST]
[*]Use lxappearance  - *modified files but no changes happened*
[*]Manually configure .gtkrc-2.0 and .config/gtk-3.0/settings.ini - *again no changes actually visible from modifyin*
[*]Modify font size in .i3/config - *changed window font but nothing else*
[*]Change font through xfce settings manager - *no actual changes visible*
[/LIST]

I feel as though I've looked up just about every forum post out there and cannot find a solution to my problem. I just want to be able to increase the font size of my terminal, but my .gtkrc-2.0 files do nothing if I modify them. Any help? Thanks

---

### Post by buzzingrobot on 2015-11-06
Which terminal are you using? Check if it enables font selection in its own preference panel.

---

