---
title: "UGS NX6 palette organization"
date: 2013-01-11
forum: Education &amp; Science
---

### Post by Tyndarus on 2013-01-11
Hello,

I've recently installed UGS NX6 under ubuntu 10.04LTS x64. It's functioning well except for the palette organization. I can't seem to `merge' palettes and windows with the main window. According to some tutorials i saw this should be possible.

Before this i also has the error 'X Toolkit Warning: No font found' showing in command window. This problem has been solved by following advice from a previous post ([http://ubuntuforums.org/archive/index.php/t-581762.html](http://ubuntuforums.org/archive/index.php/t-581762.html) : 
[INDENT]For some reason these files aren't created at the installation, which results in st trange window behavior (ex no text,...).Create a map /usr/lib/X11/app-defaults, and copy Ugmenu10_default and  Ugnx5_default in this map and rename them Ugmenu10 and Ugnx5.
[/INDENT]Now there's no more errors in command window, but I can't seem to merge drawing windows and other into the main window (no buttons in top bar and i didn't find anything in any menu (like preferences...)), so I assume it's also caused by misplacement of a certain configuration file.

The attachment shows that the window top bars only show the top bar with the name, right click gives same menu as any other X-server window (minimize, maximize, move, resize, move to workspace...)

Has anyone experienced this problem?

kind regards,
Dieter

---

