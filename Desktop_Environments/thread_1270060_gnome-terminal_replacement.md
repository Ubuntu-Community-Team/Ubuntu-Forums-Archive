---
title: "gnome-terminal replacement"
date: 2009-09-19
forum: Desktop Environments
---

### Post by Esthellin on 2009-09-19
Currently using gnome-terminal, but want a lightweight replacement.

Needed features:
Japanese support (both output and input(already using SCIM (anthy) for other programs))
Tabs

I am using Ubuntu Jaunty and looking for a lightweight fast version. Gnome-terminal is way too bulky and slow; having uneeded options.
Have tried xterm but it won't let me input japanese text with scim (Ctrl-Space shortcut key doesn't work)
Multi-aterm had the tab support but could not show the Japanese characters.

I was thinking of Xfce-term but it requires other packages, resulting in the same usage space as gnome-terminal.

Having tabs would be preferred but is not essential.

---

### Post by kerry_s on 2009-09-19
roxterm? rxvt-unicode?

---

### Post by earthpigg on 2009-09-19
i have no idea if [LXTerminal]("http://wiki.lxde.org/en/LXTerminal") supports japanese, but ill toss that into the pot as well.

---

### Post by Esthellin on 2009-09-19
> **kerry_s said:**
> roxterm? rxvt-unicode?

Roxterm. Where have you been all my life? -drools-
Just as its description says. Gnome-terminal but smaller footprint. It allowed the japanese input and output and the tab-ness.
-thumbs up-

Thanks kerry_s!

---

### Post by Esthellin on 2009-09-20
Currently using roxterm. However, it does not have true transparency, like gnome-terminal does when using metacity as the compositing manager.
I have checked the version and their Sourceforge site has a more updated version of roxterm, including true transparency. Any reason why this is not in the ubuntu repositories accessible via synaptic?

---

### Post by Esthellin on 2009-09-20
There was also another bug, not sure if it is roxterm gnome-session.

I don't have gnome-panel running when on the laptop. Sometimes I run the command from the terminal to see its current layout or the network then close it.

I did this the other day, but after closing the command (Ctrl-C in the terminal), gnome-panel closed but a new instance of roxterm was created. What the?

---

### Post by kerry_s on 2009-09-20
sounds like you need to keep looking for a terminal that makes you happy.

**apt-cache search "terminal emulator" **
there are lot to choose from, have you tried "xfce4-terminal"?

ubuntu is a snapshot distro, updated programs are in next releases, current releases get frozen except for security fixes.


i use rxvt, i just need light, this rigs old 450mhz 256mb ram.

---

### Post by Esthellin on 2009-09-20
"450mhz 256mb ram"? -whistles- Your computer isn't running, it is crawling.

I haven't tried Xfce-terminal yet. To use it, I have to install alot of other libs. I looked at the size, and it ends up using the same space as gnome-terminal.

I think you are right with the snapshot comment. Maybe I should switch distros...
Mind you, considering I only use a handful of programs and all of them from the terminal, maybe I should try something like PuppyLinux or something like that.

---

### Post by kerry_s on 2009-09-20
> "450mhz 256mb ram"? -whistles- Your computer isn't running, it is crawling.

:lolflag:
actually no, it's not, i run a trim system, use fast programs. i idle in around 50/245 so i got plenty of resources, just using the web browser, i'm still less than 100 mem.

---

### Post by Maravilha on 2009-09-21
I kinda like [tilda]("http://tilda.sourceforge.net/wiki/index.php/Main_Page") and [guake]("http://trac.guake-terminal.org/") Though I am also not sure if they support japanese fonts

---

### Post by Esthellin on 2010-07-21
I am experimenting with a new one:rxvt-unicode. So far it has everything I need, but I have found a little...hiccup.
I know that it is not a transparency, because it appears with both transparency and without.

With both w3m, nvlcm and other programs, there can appear "pixel rubbish" at the borders of the screen.

For example, if I chose a certain font that can't fit the entire screen (e.g. there is half a character worth of space at each border), sometimes when I scroll or I move the windows around, some of the screen output appears in these borders. When I checked with transparency on, initally these borders existed but non-transparent (they were the defautl background colour) After something ( I don't know) the whole window was transparent, but the background image was distorted in the areas of these borders.

It is like only the area that characters fit is being refreshed correctly and not these extra portions.

Anyone shed some light on this?

See attached picture for the 'rubbish' below the nvlcm window.

---

