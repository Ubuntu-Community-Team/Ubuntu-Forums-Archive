---
title: "WoW, KDE and Beryl"
date: 2007-04-22
forum: Gaming &amp; Leisure
---

### Post by heepster on 2007-04-22
Hi
First of all sorry for bad english I am from Germany...

I have a Problem with World of Warcraft and the KDE Kicker, because Kicker overlays the WoW Window.
I found the Problem at Beryl, but I want to use it's Cube Desktop on WoW.

I could make Kicker allow to be overlayed by Apps, but it would :mad: me on Desktop work.

Maybe one of you has a solution

[IMG]http://img227.imageshack.us/img227/7714/bildschirmphoto1yh0.png[/IMG]

---

### Post by hikaricore on 2007-04-22
Set WoW to run in Windowed mode (you will need to do this in d3d mode or manually in the Config.wtf file), then right click on the titlebar go into Advanced and click "Keep Above Others". **
(this is the only way I can think of at the moment to keep it above the kicker effectivly and you'll need to "Pin" it each time you restart it, someone feel free to offer a better suggestion)

Though I don't suggest running WoW while using Beryl unless you have a super amazing system.

**The keep above others assumes you're using aquamarine with beryl which keeps your standard windowframes but still allows beryl effects, I forget what the beryl equivalent of this is, probably Pin or something of the sort.

---

### Post by heepster on 2007-04-22
Thanks but I've solved the Problem:
    *

      For Beryl/Compiz users with gnome pannel showing on top of World of Warcraft start the game in windowed mode. Either by adding  -windowed  to your command line starting WoW, or add  SET gxWindow "1"  to wtf/Config.wtf.

Runs very well

---

### Post by thom_raindog on 2007-04-22
What is funny: This fix does not work for me... Nor does disabling Desktop-Effects...??
How do I get my (freshly installed) WoW to run in fullscreen on my (freshly installed) Ubuntu 7.04?

---

### Post by hikaricore on 2007-04-22
this thread wasn't about running wow fullscreen.... and it wasn't about gnome..

---

