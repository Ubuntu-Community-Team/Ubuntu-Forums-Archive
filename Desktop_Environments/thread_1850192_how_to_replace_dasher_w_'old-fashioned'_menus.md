---
title: "how to replace dasher w/ 'old-fashioned' menus?"
date: 2011-09-26
forum: Desktop Environments
---

### Post by johnherron on 2011-09-26
Hello, everyone.   :)

Just last week got a new box with Ubuntu 11.04 preloaded, replacing my former 3-yr old Kubuntu box (harddisk died....).

What bothers me most is the Application launcher (believe it's called Dasher?); for my taste very invasive and rather unpractical.

Tried to discover a way to disable it and replace it with an 'old-fashioned' drop-down or pop-up set of menus, but failed miserably.

Is it at all feasible? If so, can anyone help?

Thanks in advance.
jdh

---

### Post by Copper Bezel on 2011-09-26
Which part are we talking about here - the Unity interface as a whole (the top panel, the dock at the left, called the "Launcher," and the new Dash menu) or just the Dash itself? They're all part of the same Compiz plugin, so you can't really have one part without the others, but you can use the classic panel interface just by logging out and selecting "Ubuntu Classic" in the box that appears under the login window after you select your user account.

If it doesn't remember your choice, you can set the default in the Login Screen Settings (under Settings > Administration in the classic menu.)

---

### Post by johnherron on 2011-09-26
Did as you suggested and now have Ubuntu Classic with no Launcher nor Dash - the top panel is still there, though, and now features a drop-down set of menus on the left-hand side; in addition there's a bottom panel with the workspaces. Thank you, Copper Bezel!

By the way: is it possible to reduce the line spacing of the menu entries? or am i asking for too much?

---

### Post by raja.genupula on 2011-09-26
hi if you want you can reduce your dash size .

Install **dconf-tools** & **open your terminal** 
Run **dconf-editor**  
at the window which will opened click at **Desktop** & in that  **Unity** then at left-hand tree Select **Desktop** as **form facto**r.

---

### Post by Copper Bezel on 2011-09-26
Cool - I'm glad that looks like it'll work for you. = ) The panel is actually a different application in Ubuntu Classic - unlike the one in Unity, it can be reconfigured and such if you like.

> By the way: is it possible to reduce the line spacing of the menu entries? or am i asking for too much?
Unfortunately, this is defined by the theme - there's no way to change it within the GUI settings - and I'm not certain which value should be changed in the theme file. If you copy the Ambiance theme folder (or whichever you're using) from /usr/share/themes to .themes in your home directory, you can modify it, and the file gtkrc under the gtk-2.0 directory defines the padding and such. I *think* it's line 48 in Ambiance's theme file, GTK menu vertical padding.

(Yeah, I know, KDE has nice little dials for these things, without editing text files.... *shrug*)

---

