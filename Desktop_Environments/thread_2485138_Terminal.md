---
title: "Terminal"
date: 2023-03-21
forum: Desktop Environments
---

### Post by AnupamMitra on 2023-03-21
My desktop environment is UBUNTU 22.04.  Since today morning I tried to open Terminal, but couldn't. Generally I open Terminal by Ctrl+Alt+t or by right click on desktop or from the Activities menu. But today there is no response from either of the options.  Till yesterday it was alright. I have not installed anything at my own. However, only changes has taken place i.e. UBUNTU PRO is enabled by default. Whether this has any relation to that? How to resolve it and/or how can I open Terminal?

---

### Post by ActionParsnip on 2023-03-21
Can you launch a different terminal. I believe xterm should be installed. If not then install it using Software Centre or press CTRL + ALT + F1 and install there in CLI using apt. Does that run OK?

---

### Post by TheFu on 2023-03-21
There are many different terminal programs.  All can be installed, at will.  Try a different one. As AP says, **xterm** is a reasonable one, provided you use English charactersets.  I think **rxvt** is another with support for unicode. These are relatively small terminal programs.

The gnome-terminal is fairly bloated, BTW and I have yet to see the point for most of the bloat. Terminals get setup once to use the font at the size with the coloring you like, then that's about it forever.  Little need to have all the menus, at least I see little reason for them.

Anyway, try a few of the 50 other terminal programs and see if any work. In general, if you can login, then the issue isn't too large, unless someone screwed with your login initialization files and broke them.

Lastly, allowing automatic updates is a dangerous thing.  If you do that, please reconsider.  How hard is it to manually patch every Friday night or sometime over the weekend?  Having changes occur without your explicit request is a productivity and security failure.

---

### Post by AnupamMitra on 2023-03-22
> **ActionParsnip said:**
> Can you launch a different terminal. I believe xterm should be installed. If not then install it using Software Centre or press CTRL + ALT + F1 and install there in CLI using apt. Does that run OK?

Thanks for your cooperation.  Yes, I had installed Xterm. But it does not suit me due to very small size of font and moreover it does not support copy-paste.  You would agree that occasionally it is required to copy big command for pasting in Terminal, but Xterm doesn't support either direct pasting or by ctrl+v. Therefore, I reinstalled Terminal after uninstalling. In this regard I found that Sakura Terminal is also a good one.

---

### Post by AnupamMitra on 2023-03-22
> **TheFu said:**
> There are many different terminal programs.  All can be installed, at will.  Try a different one. As AP says, **xterm** is a reasonable one, provided you use English charactersets.  I think **rxvt** is another with support for unicode. These are relatively small terminal programs.

The gnome-terminal is fairly bloated, BTW and I have yet to see the point for most of the bloat. Terminals get setup once to use the font at the size with the coloring you like, then that's about it forever.  Little need to have all the menus, at least I see little reason for them.

Anyway, try a few of the 50 other terminal programs and see if any work. In general, if you can login, then the issue isn't too large, unless someone screwed with your login initialization files and broke them.

Lastly, allowing automatic updates is a dangerous thing.  If you do that, please reconsider.  How hard is it to manually patch every Friday night or sometime over the weekend?  Having changes occur without your explicit request is a productivity and security failure.

Thanks for your cooperation like earlier occasions.  I have noted your suggestions for future compliance.

---

### Post by TheFu on 2023-03-22
> **AnupamMitra said:**
> Thanks for your cooperation.  Yes, I had installed Xterm. But it does not suit me due to very small size of font and moreover it does not support copy-paste.  You would agree that occasionally it is required to copy big command for pasting in Terminal, but Xterm doesn't support either direct pasting or by ctrl+v. Therefore, I reinstalled Terminal after uninstalling. In this regard I found that Sakura Terminal is also a good one.

xterms fully support select/paste using normal X/Windows.

**If you are the keyboard, you are doing it the hard way.**

* **Select** the text (left-mouse) - don't forget that dbl-click will select a word, triple-click the entire line and that you can select a word then drag left to get exactly the beginning you want.  Don't select anything else.  This select action places the selection into the X-buffer.
* Use the middle mouse button to **paste**.  Pasting 1 or 50 times is possible, until the X-buffer gets filled with a new value.

If you have multi-line paste needs, like into a bash term and don't want to be hassled with the recently introduced paste-protection, that can be disabled 
```
$ more ~/.inputrc
set enable-bracketed-paste off # retain old select/paste behavior
```

If the xterm font to too small, there are multiple ways to handle that.
a) <cntl>+ right click inside the xterm window somewhere - choose a larger font.
b) pass in the font and size when you startup the xterm process(es). I use this when I first start a new GUI session:
```
XTERM_OPTS="-u8 -fs 12 -fa Monospace -sb -fg green -bg black"
xterm $XTERM_OPTS -geometry 78x9+78+0 &
xterm $XTERM_OPTS -geometry 80x21+73+82 &
xterm $XTERM_OPTS -geometry 80x25+0+117 &

```
In that same script, I'll connect to 4 other systems, placing each terminal in a specific place on the screen.

---

