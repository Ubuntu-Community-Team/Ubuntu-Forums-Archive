---
title: "Borderless, decorationless terminal... [examples]"
date: 2006-07-09
forum: Desktop Environments
---

### Post by roostishaw on 2006-07-09
Hello,
What command would I use, when launching aterm, to get my terminal to look something like these? I'm using gnome, and have nautilus set to NOT draw my desktop (if that matters).

[http://www.lynucs.org/index.php?screen_id=27634931844ae6d97ef456&p=screen](http://www.lynucs.org/index.php?screen_id=27634931844ae6d97ef456&p=screen)
[http://www.lynucs.org/index.php?screen_id=89154308844145c916bcbc&p=screen](http://www.lynucs.org/index.php?screen_id=89154308844145c916bcbc&p=screen)
[http://www.lynucs.org/index.php?screen_id=291969276440d99928f4a0&p=screen](http://www.lynucs.org/index.php?screen_id=291969276440d99928f4a0&p=screen)
[http://www.lynucs.org/index.php?screen_id=17890464743df447e3c247&p=screen](http://www.lynucs.org/index.php?screen_id=17890464743df447e3c247&p=screen)

Any help is appreciated,
Thanks!

---

### Post by Anduu on 2006-07-09
I believe you are looking for this:

[http://www.ubuntuforums.org/showthread.php?t=81727](http://www.ubuntuforums.org/showthread.php?t=81727)

---

### Post by DJ Scribblinni on 2006-07-09
Heres the code for the complete transparency and no borders 
```
Eterm --trans -g 90x20+0+360 -L 10000 -b black -f  white --shade 0 -x --borderless --scrollbar 0 --buttonbar 0 -c grey89
```

Go from there and shade it out and change colors, and poof, one step closer to that perfect desktop...

---

### Post by roostishaw on 2006-07-09
Thanks to both of you for the replies, but I opted to use devilspie instead.

[http://img84.imageshack.us/img84/2787/screenshot5jf.png](http://img84.imageshack.us/img84/2787/screenshot5jf.png)

If someone wants to know how I got that, just ask. But now the trouble is that I can't figure out what command I put in the devilspie .ds file to make it so that the matched window won't minimize when I click the 'show desktop' button.

Also, if you look at the screenshot, how would I spawn a terminal *exactly* like the one on the bottom left, but on the right side? I can't seem to figure out how... My DesktopConsole.ds is as follows:
```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (pin)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+30+485")
                (geometry "570x400")
        )
)
```
And my relevant starup entries are as follows:
```
gnome-terminal --window-with-profile=DesktopConsole
```
```
devilspie
```

Anyone?

---

### Post by roostishaw on 2006-07-09
bump for the huge update to my last post
:)

---

