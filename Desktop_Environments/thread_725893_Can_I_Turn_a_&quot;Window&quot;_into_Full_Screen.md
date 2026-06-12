---
title: "Can I Turn a &quot;Window&quot; into Full Screen"
date: 2008-03-16
forum: Desktop Environments
---

### Post by Wyld on 2008-03-16
What I'm after, is a way to force my window over everything else, remove its decorations, and set it at 0,0 

I am running Neverwinter Nights, and have it working on one desktop whilst I can view IRC or the Web on the other desktop using twinview .. but without turning off the window decorations, I can't see the button bar on the bottom of the screen.

Any suggestions on how I can take control over the window?

Mark

---

### Post by kellemes on 2008-03-16
Well.. your question inspired me to tackle this issue..
I'm not a Gnome-user myself so it may be I'm missing some more obvious solution here..
Anyway, using [DevilsPie]("http://burtonini.com/blog/computers/devilspie") I got the result you're asking..

```
sudo apt-get install devilspie
mkdir ~/.devilspie
vim ~/.devilspie/maximize.ds
```
In this file I have the following lines..
```
(if
(is (application_name) "Firefox")
(begin
(fullscreen)
)

```
This works for Firefox, it will cover the hole screen, obviously you need to replace "Firefox" with the name of the neverwinter-window.

A couple of links that got me going..
[http://foosel.org/linux/devilspie]("http://foosel.org/linux/devilspie")
[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/]("http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/")

---

### Post by spupy on 2008-03-16
Try this command:
```
wmctrl -r :SELECT: -b toggle,fullscreen
```
and the cursor turns into a plus, click the window with it.
The program called wmctrl is very powerful for managing windows. 
I have no idea how will it get fullscreen-ed on gnome, i tested it on fluxbox.

---

### Post by x1a4 on 2008-03-17
> **spupy said:**
> I have no idea how will it get fullscreen-ed on gnome, i tested it on fluxbox.

It should.  I just tested in AfterStep and XFCE and it works, so I see no reason why it wouldn't work with the Gnome's window manager.

---

