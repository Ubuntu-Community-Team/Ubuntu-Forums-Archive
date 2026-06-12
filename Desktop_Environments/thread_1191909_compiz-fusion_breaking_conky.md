---
title: "compiz-fusion breaking conky"
date: 2009-06-19
forum: Desktop Environments
---

### Post by staticanime on 2009-06-19
Hey, I need some help, Compiz-Fusion is putting an odd box around conky.
[This]("http://ubuntuforums.org/showpost.php?p=4231327&postcount=7") post kinda helped, but it disabled shadows on everything, I want to keep shadows on most windows, I just want to disable them on conky, can anyone tell me what I should put into ccsm -> Window Decoration -> Shadow Windows? I have any -conky atm

EDIT: I launch conky at start-up with a script that delays conky's launch for 20 seconds after login to give Compiz time to start

---

### Post by Tibuda on 2009-06-19
Add this before TEXT in your .conkyrc:
```
own_window_title theconky
```
And change the "shadow windows" in your compiz decoration plugin to
```
any & !(title=theconky)
```

---

### Post by staticanime on 2009-06-19
> **danielrmt said:**
> Add this before TEXT in your .conkyrc:
```
own_window_title theconky
```
And change the "shadow windows" in your compiz decoration plugin to
```
any & !(title=theconky)
```

No joy, it's still shadowing it. I can export my Compiz-Fusion config and attach it and my conky config it that helps?

---

### Post by Tibuda on 2009-06-19
I think the conkyrc is enough.

---

### Post by staticanime on 2009-06-19
Renamed it to conkyrc.txt and attached it

---

### Post by Tibuda on 2009-06-19
No shadows here...

Well, by reading your file, I would suggest you to uncomment this line:
```
#own_window_hints **undecorated**,below,sticky,skip_taskbar,skip_pager
```
I'm no conky expert, but I think it has something to do with this "undecorated" window hint.

If it does not work, a screenshot of the window decorations plugin in compiz may help.

EDIT: No, I'm wrong, uncommenting that line won't work:
> [If own_window is yes, you may use these window manager hints to affect the way Conky displays. Notes: Use own_window_type desktop as another way to implement many of these hints implicitly. If you use own_window_type override, window manager hints have no meaning and are ignored.]("http://conky.sourceforge.net/config_settings.html")

---

### Post by staticanime on 2009-06-19
> **danielrmt said:**
> No shadows here...

Well, by reading your file, I would suggest you to uncomment this line:
```
#own_window_hints **undecorated**,below,sticky,skip_taskbar,skip_pager
```
I'm no conky expert, but I think it has something to do with this "undecorated" window hint.

If it does not work, a screenshot of the window decorations plugin in compiz may help.

It doesn't make any difference whether that line is commented or not. The only changes from default on the Window decorations plugin are the ones I used from [this]("http://webupd8.blogspot.com/2009/05/ubuntu-embed-terminal-into-you-desktop.html") guide to put a terminal on the desktop.

---

### Post by Tibuda on 2009-06-19
I have no idea what to do. Maybe the people in the [conky thread]("http://ubuntuforums.org/showthread.php?t=281865") can help you more.

---

### Post by staticanime on 2009-06-19
> **danielrmt said:**
> I have no idea what to do. Maybe the people in the [conky thread]("http://ubuntuforums.org/showthread.php?t=281865") can help you more.

I don't think it's a conky problem, because I did get it to go away by setting any -conky in the Shadow windows area in the Window Decorations plugin in compiz. but that turns off ALL shadows, which I don't want (i'm now partial to the drop-shadow under my menu bar.

EDIT: Attached my compiz config too

---

