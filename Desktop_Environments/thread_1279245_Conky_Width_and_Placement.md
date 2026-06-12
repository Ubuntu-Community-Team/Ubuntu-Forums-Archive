---
title: "Conky Width and Placement"
date: 2009-09-30
forum: Desktop Environments
---

### Post by Lukios on 2009-09-30
I have googled this and come up with nothing. I need to make my horizontal conky go 100% width of the monitor. I understand that I can manually set the width to the size of my current monitor, but I want  simply be able to put this .conkyrc on another computer without having to change the width value. Also, I would like to know how to make conky display itself above all windows when I call it via terminal.

Thanks in advance

---

### Post by Lukios on 2009-10-02
anyone?

---

### Post by Lukios on 2009-10-06
can anyone at least tell me if it is possible?

---

### Post by Sarai the Geek on 2009-10-07
To the best of my knowledge, it's not. You can use minimum_size to set the size to fit exactly to your current monitor, but I don't know of a variable that will automatically change the size of the conky. I would imagine that functionality wouldn't be difficult to add if you would be so inclined as to contact the devs about it.

---

### Post by stinkeye on 2009-10-07
> **Lukios said:**
> I have googled this and come up with nothing. I need to make my horizontal conky go 100% width of the monitor. I understand that I can manually set the width to the size of my current monitor, but I want  simply be able to put this .conkyrc on another computer without having to change the width value. Also, I would like to know how to make conky display itself above all windows when I call it via terminal.

Thanks in advance
To display conky above other windows change this setting above "TEXT"
own_window_hints undecorated,[COLOR="DarkRed"]below[/COLOR],skip_taskbar,skip_pager
To
own_window_hints undecorated,[COLOR="Blue"]above[/COLOR],skip_taskbar,skip_pager

Also if you have ```
own_window_type [COLOR="DarkRed"]override[/COLOR]
```
change it to ```
own_window_type [COLOR="Blue"]normal[/COLOR]
```
because when set to override it ignores "own_window_hints", and defaults to below.

This thread here will give you a faster response to any further conky
questions you may have:
[_[COLOR="DarkRed"]Post your .conkyrc files w/ screenshots[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=281865&page=964")

---

### Post by Lukios on 2009-10-08
Thank you stinkeye, that worked perfectly. I will post my other question on that thread you suggested.

---

