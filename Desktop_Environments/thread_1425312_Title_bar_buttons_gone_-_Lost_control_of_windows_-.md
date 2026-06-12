---
title: "Title bar buttons gone - Lost control of windows -Jaunty 9.04"
date: 2010-03-08
forum: Desktop Environments
---

### Post by Sky Aisling on 2010-03-08
Hello,
I've searched the forum for an answer to this but so far no teddy bear.  I've gone to Xfce website but unable to negotiate windows enough to log in.  Any help is appreciated.  I've lost control of Xfce4 windows on Jaunty 9.04:


[LIST]
[*]Title bar buttons to diminish, expand, quit are gone
[*]Windows stick to upper left-hand corner of screen
[*]Windows overlay other windows with no way to move them aside
[*]When I access *file* or *edit* drop down goes behind window (same for right click)
[*]When I go to Applications/settings/Xfce4 settings, only the frame of the apps appear but no content shows (I was attempting to open *window settings* and *window tweaking* apps)
[/LIST]
I'm willing to reinstall Xfce4 if someone can tell me how to do that.

Thanks in advance.

---

### Post by rory526 on 2010-03-08
have you tried ctrl + alt + backspace? Should restart X windows.

---

### Post by Sky Aisling on 2010-03-08
Just tried *control*, *alt*, * backspace*   Nothing happens.

---

### Post by Sky Aisling on 2010-03-09
Situation is Solved.  I contacted the folks at Xfce [http://www.xfce.org/](http://www.xfce.org/).
They suggested that the windows manager wasn't running and gave me a terminal command that resolved the situation.

The terminal command is:  ***xfwm4 --replace --daemon***

---

### Post by jebradley on 2011-10-01
Thank you, thank you.

I had recently been using kde on my ubuntu oneric desktop, because I'd lost the ability to move any windows, and the buttons had disappeared. I couldn't figure out anything that I'd done, and neither reinstallation, nor copying the .config/xfce4 directory files from a working system helped.

The 'xfwm4 --replace --daemon' solved the problem, which makes xfce usable again. Life is wonderful again.

---

