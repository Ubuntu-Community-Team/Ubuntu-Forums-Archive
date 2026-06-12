---
title: "Gnome Compatible Window Managers"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by kshane on 2007-10-20
What other window managers are compatible with Gnome?  I found a link that shows a list of them, but very little about compatibility.  Any one know what others are compatible?  I'm kinda tired of Metacity and, until ATI releases the new driver, there's not much to do with Gnome...

All the Forum threads I've found are either old or are for jusdt doing the Compiz thing...

Kevin

---

### Post by Nutty Hiker on 2007-10-20
I don't know what you want in a Window Manager, but I love fluxbox.  It's light, fast, highly customizable...

It's great.

---

### Post by kshane on 2007-10-20
> **Nutty Hiker said:**
> I don't know what you want in a Window Manager, but I love fluxbox.  It's light, fast, highly customizable...

It's great.

Thanks for the reply!  I'm really just getting bored with Metacity, so looking for some change and a little pizazz

Kevin..

---

### Post by kshane on 2007-10-20
> **Nutty Hiker said:**
> I don't know what you want in a Window Manager, but I love fluxbox.  It's light, fast, highly customizable...

It's great.

Hey Nutty Hiker, hope you're still around...

I installed fluxbox and I have no menu (except for the panel)...  Got any hints on this one?  :confused:

Kevin

---

### Post by Nutty Hiker on 2007-10-20
Yep, I sure do.

First, you need to go back into the Gnome window manager.  While there open up a text editor (like gedit, for example).  Open up /home/_you_/.fluxbox/menu

Look at the structure.

What I would put first in there, after the top and before the bottom, is this:

```

[submenu](apps) {}
       [include] (/etc/X11/fluxbox/menudefs.hook)
[end]

```

This should autopopulate the menu with default debian applications.  Save it, log out, and then log back in to fluxbox.  Right-click and you should see the submenu item named "apps."  It should be filled with many applications.  After that you can customize the menu however you want it to be.

Let me know how it works.  Here's a screen shot of my desktop.

---

### Post by kshane on 2007-10-20
> **Nutty Hiker said:**
> Yep, I sure do.

First, you need to go back into the Gnome window manager.  While there open up a text editor (like gedit, for example).  Open up /home/_you_/.fluxbox/menu

Look at the structure.

What I would put first in there, after the top and before the bottom, is this:

```

[submenu](apps) {}
       [include] (/etc/X11/fluxbox/menudefs.hook)
[end]

```

This should autopopulate the menu with default debian applications.  Save it, log out, and then log back in to fluxbox.  Right-click and you should see the submenu item named "apps."  It should be filled with many applications.  After that you can customize the menu however you want it to be.

Let me know how it works.  Here's a screen shot of my desktop.

***SWEET!!!***  Thanks a lot...  I'll get back with ya!

Kevin

---

### Post by kshane on 2007-10-20
All I got was a tab that said "APPS" with nothing after it.  Below is the file...

```

[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)

[submenu](apps) {}
       [include] (/etc/X11/fluxbox/menudefs.hook)
[end]
[end]

```

Any ideas?

Kevin

---

### Post by Nutty Hiker on 2007-10-20
Odd. Here is my menu:
```

[begin] (fluxbox) {}
   [nop] (quick links)
   [separator]
   [exec] (firefox) {/usr/bin/firefox}
   [exec] (thunderbird) {/usr/bin/mozilla-thunderbird}
   [exec] (xmms) {/usr/bin/xmms} 
   [exec] (xterm) {xterm -geometry 100x30}
   [exec] (gedit) {/usr/bin/gedit}
   [separator]
   [submenu](apps) {}
       [include] (/etc/X11/fluxbox/menudefs.hook)
    [end]
    [separator]
    [submenu] (help) {}
        [exec] (info) { x-terminal-emulator -T "Info" -e info}
    [end]
    [config] (configuration) {}
    [submenu] (styles) {}
        [stylesdir] (/usr/share/fluxbox/styles) {}
        [stylesdir] (~/.fluxbox/styles) {}
   
   [end]
    [submenu] (backgrounds) {}
     [wallpapers] (~/.fluxbox/backgrounds)
   [end]
    [workspaces] (workspaces) {}
    [reconfig] (reconfigure) {}
    [restart] (restart) {}
    [exit] (exit) {}
[end]

```
Back up your original and try that one.

---

### Post by kshane on 2007-10-20
I found a bunch of sample configuration files on fluxboxes web site and copied them.  It was set up for KDE, so I just edited a few things to reflect my software and it seems to work.  I am using firefox and it was setup for firebird...  I started firefox from my menu changes...

Thanks you very much for the assist!  Got me going.  I have a bunch of modifications to do now, but, *IT'S WORKING!!!*

:lolflag:

Thanks again!

Kevin

---

### Post by Nutty Hiker on 2007-10-20
Glad you got it started!  If you don't mind tinkering and like having a clean interface, fluxbox is for you.  

Notice how much faster it is?

Anyway, have fun!

---

### Post by Kossilar on 2007-10-21
Of all the WM's I've tried, Fluxbox is definitely my favorite so far, I'm thinking about giving Enlightenment a spin though, just to try it out. But Fluxbox is my current favorite. The only thing its lacking is some delicious desktop effect eye candy. :)

---

### Post by kshane on 2007-10-21
> **Nutty Hiker said:**
> Odd. Here is my menu:
```

[begin] (fluxbox) {}
   [nop] (quick links)
   [separator]
   [exec] (firefox) {/usr/bin/firefox}
   [exec] (thunderbird) {/usr/bin/mozilla-thunderbird}
   [exec] (xmms) {/usr/bin/xmms} 
   [exec] (xterm) {xterm -geometry 100x30}
   [exec] (gedit) {/usr/bin/gedit}
   [separator]
   [submenu](apps) {}
       [include] (/etc/X11/fluxbox/menudefs.hook)
    [end]
    [separator]
    [submenu] (help) {}
        [exec] (info) { x-terminal-emulator -T "Info" -e info}
    [end]
    [config] (configuration) {}
    [submenu] (styles) {}
        [stylesdir] (/usr/share/fluxbox/styles) {}
        [stylesdir] (~/.fluxbox/styles) {}
   
   [end]
    [submenu] (backgrounds) {}
     [wallpapers] (~/.fluxbox/backgrounds)
   [end]
    [workspaces] (workspaces) {}
    [reconfig] (reconfigure) {}
    [restart] (restart) {}
    [exit] (exit) {}
[end]

```
Back up your original and try that one.

I put your menu file in place and it works GREAT!  Thanks again!  Now to play with it...

Kevin

---

### Post by Nutty Hiker on 2007-10-21
> **Kossilar said:**
> Of all the WM's I've tried, Fluxbox is definitely my favorite so far, I'm thinking about giving Enlightenment a spin though, just to try it out. But Fluxbox is my current favorite. The only thing its lacking is some delicious desktop effect eye candy. :)

Hey, play around.  That's the fun part of Linux!

---

