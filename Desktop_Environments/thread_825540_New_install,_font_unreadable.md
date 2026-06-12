---
title: "New install, font unreadable"
date: 2008-06-11
forum: Desktop Environments
---

### Post by yodermk on 2008-06-11
Hi, I just installed Xubuntu on a crappy emachines box.

It is connected to a 36" TV, 1300x768 (or something like that).

All UI fonts, both for the installer and now for the installed system, are virtually unreadable.  I have to hold my eye right up to the TV and squint, and then I can sort of read some of it, with pain.

There is space available in the elements for regular text, just the text itself is tiny. There is empty space around the text.

Other than that, the graphics on the screen look as to be expected. Also, when I load Firefox and load a web page, the web page is rendered with a normal readable font.  It's only the UI elements.

How can this be fixed?  I stumbled through the options and couldn't find anything, but keep in mind that I may have missed something because I couldn't read it.

Thanks!

---

### Post by yodermk on 2008-06-11
More ... During the install and on first boot, the usable screen filled the TV.

When I edited xorg.conf to add font paths (which I found on the net), it was just full of generic card and monitor info.  When I rebooted, it said it came up in low graphics mode, just 640x480 I think, and only covered part of the center of the screen. The fonts were just as bad.

I wonder what caused the change. All I did was add font paths!

---

### Post by yodermk on 2008-06-14
Ok, same computer, this time with the 15" LCD that came with it, and it works fine.  I guess with the LCD it didn't get the resolution correctly. Still kind of strange.

---

### Post by bric on 2008-06-14
I had a similar issue with my resolution not detecting correctly and yet it worked fine with a regular monitor connected.  As it turned out for me the solution was annoyingly simple (annoyingly because of the many days I spent fiddling with modelines and more trying to make things work).

Anyhow, the motherboard has an hdmi out and a vga out.  I was using the hdmi out to the HDTV and that was fine until it wasn't (i.e., worked ok for a while then suddenly my problems were more or less as you described).  I tried to fix it to no avail.  A regular CRT monitor connected via vga was fine.  The solution was to reseat (unplug / re-plug) the hdmi cable at the back of my computer.

Just in case it's of help.

---

