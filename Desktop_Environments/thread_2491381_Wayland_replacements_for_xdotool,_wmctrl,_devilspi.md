---
title: "Wayland replacements for xdotool, wmctrl, devilspie2"
date: 2023-10-06
forum: Desktop Environments
---

### Post by Paddy Landau on 2023-10-06
For my own purposes, I've been documenting Wayland replacements for [FONT=courier new]xdotool[/FONT], [FONT=courier new]wmctrl[/FONT] and [FONT=courier new]devilspie2[/FONT], all of which I use extensively (Ubuntu 22.04, running X.Org instead of Wayland).

I've created a table, which I'll add to when (if!) replacements become available, or if someone posts suitable replacements in the comments.

For now, this table is mostly empty, meaning that I still cannot use Wayland without considerable inconvenience. I have to stick to X.Org for now.


[TABLE="class: grid, width: 100%, align: center"]
[TR]
[TD]**X.Org tool**[/TD]
[TD]**Wayland equivalent**[/TD]
[/TR]
[TR]
[TD][FONT=courier new]xdotool [/FONT]…[FONT=courier new] --clearmodifiers[/FONT][/TD]
[TD]Unavailable[/TD]
[/TR]
[TR]
[TD][FONT=courier new]xdotool type [/FONT]*[pattern]*[/TD]
[TD][FONT=courier new]ydotool type [/FONT]*[pattern]*
**Comments:**
[FONT=courier new]ydotool[/FONT] (for now) needs to be manually installed, configured and enabled.
The one in the standard repositories (22.04) is badly out of date.[/TD]
[/TR]
[TR]
[TD][FONT=courier new]xdotool key [/FONT]*[key]*
E.g.
[FONT=courier new]xdotool key super+F1[/FONT][/TD]
[TD][FONT=courier new]ydotool key [/FONT]*[key]*[FONT=courier new]:1 [/FONT]*[key]*[FONT=courier new]:0[/FONT]
E.g.
[FONT=courier new]ydotool key 125:1 59:1 59:0 125:0[/FONT]
**Comments:**
**&#8203;**[FONT=courier new]ydotool[/FONT] uses key codes instead of symbolic names.
Get the codes from file [FONT=courier new]/usr/include/linux/input-event-codes.h[/FONT]
You usually have to be precise about key-down ([FONT=&amp]:1[/FONT]) and key-up ([FONT=&amp]:0[/FONT]).[/TD]
[/TR]
[TR]
[TD][FONT=courier new]xdotool search --pid=[/FONT]*[pid]*
[FONT=courier new]xdotool search --name [/FONT]*[name]*
[FONT=courier new]xdotool search --onlyvisible [/FONT]…[/TD]
[TD]Unavailable[/TD]
[/TR]
[TR]
[TD][FONT=courier new]xdotool getwindowfocus
xdotool getwindowfocus getwindowname
xdotool getactivewindow
xdotool windowfocus
xdotool windowraise
xdotool windowmove [/FONT]*[window ID][edge]*[FONT=courier new]% y[/FONT][/TD]
[TD]Unavailable[/TD]
[/TR]
[TR]
[TD][FONT=courier new]wmctrl -d
wmctrl -i -a [/FONT]*[window ID]*[FONT=courier new]
wmctrl -i -r [/FONT]*[window ID]*[FONT=courier new] -b add,maximized_vert
wmctrl -i -r [/FONT]*[window ID]*[FONT=courier new] -b add,skip_taskbar
wmctrl -i -r [/FONT]*[window ID]*[FONT=courier new] -t [desktop][/FONT][/TD]
[TD]Unavailable[/TD]
[/TR]
[TR]
[TD][FONT=courier new]devilspie2[/FONT][/TD]
[TD]Unavailable[/TD]
[/TR]
[/TABLE]


This is a pretty poor show, unfortunately. I hope that it improves massively before X11 finally sees its final deprecation. It has served us well, and will deserve its retirement.

---

### Post by TheFu on 2023-10-06
X11 isn't going anywhere.  I haven't seen any solution for UNIX or BSD that is ready.

Don't know if you saw that a serious X11 bug was uncovered a few days ago that has been around a long time. Just another reason why X11 needs to have all remove connections go through ssh tunnels, not direct.

---

### Post by Paddy Landau on 2023-10-07
> **TheFu said:**
> X11 isn't going anywhere.  I haven't seen any solution for UNIX or BSD that is ready.
Thanks. Do you know if people are working on solutions? ydotool isn't even half-baked compared to xdotool.
> **TheFu said:**
> Don't know if you saw that a serious X11 bug was uncovered a few days ago that has been around a long time. Just another reason why X11 needs to have all remove connections go through ssh tunnels, not direct.
I didn't see that. (I presume that you meant "remote", not "remove"?) I have read many items on the 'net talking of X11's security flaws in general.

---

### Post by TheFu on 2023-10-07
There will never be 100% replacements for all those listed desires. That's because many of the things that X11 allows are possible due to poor security. Wayland would need to write specialized code to allow many of them, while not violating DRM agreements. Seeks that support for DRM video is more important than usability. An argument each way is possible.  In general, better security is best for all of us, right?

---

### Post by Paddy Landau on 2023-10-07
> **TheFu said:**
> There will never be 100% replacements for all those listed desires. That's because many of the things that X11 allows are possible due to poor security. Wayland would need to write specialized code to allow many of them, while not violating DRM agreements. Seeks that support for DRM video is more important than usability. An argument each way is possible.  In general, better security is best for all of us, right?
Of course, I would agree with that.

And yet, ydotool is able to emulate typing and pressing other keys, as well as emulating the mouse. Is it too much to ask to be able to manipulate windows as well? Simple things that make my life massively easier, such as automatically positioning my Gedit window when I open it, because it never remembers where I put it. Or automatically sizing my Gnome terminal to maximum height, because it loves to make itself shorter and shorter as I open and close tabs.

A system that makes life harder than the older system is less secure than the older one, for the same reason why forcing people to change their password every two months is less secure than letting them keep their password. In other words, I'm not going to change to Wayland until it's usable for me.

Luckily, some apps still work, such as my password manager (KeepassXC). But that's not enough, by any means.

---

### Post by vanadium on 2023-12-05
One of the issues is that Wayland is fragmenting. While tools for Xorg would work on any desktop, each Wayland compositor has its own set of protocols.

Following items are valid for Gnome Desktop only.

The extension "[Run or raise](https://extensions.gnome.org/#sort=relevance)"  by e2rd covers for the tool "jumpapp", a bash script that relies on "wmctrl" to implement run or raise style shortcut keys, i.e., a shortcut combination that brings the application in the foreground if it is already running, or otherwise starts it up.

Functionality to automatically move a window to a specific workspace (one of the possibilities of devilspie) is provided by the extension [Auto Move Windows](https://extensions.gnome.org/extension/16/auto-move-windows/) by fmuellner.

Other extensions open possibilities for custom scripting.  ([Window Calls](https://extensions.gnome.org/extension/4724/window-calls/) by domandoman and [Window Calls Extended](https://extensions.gnome.org/extension/4974/window-calls-extended/) by hseliger) expose dbus calls in Gnome Shell that allow to manipulate windows from the command line (resize, move to another workspace, etc). The extension [Activate Window By Title](https://extensions.gnome.org/extension/5021/activate-window-by-title/) by lucaswerkmeister allows to activate a window, whereas the extension [Focused Window D-Bus](https://extensions.gnome.org/extension/5592/focused-window-d-bus/) by flexagoon allows to retrieve the title an class of the currently active window.

For me, having ydotool and wl-clipboard for expanding text snippets, and run-or-raise for launching/switching to applications, has been enough to make the move to Wayland. I am lacking window manipulation facilities, but I can live with that. I mostly use applications full screen, and most do remember that position. Evince annoyingly cannot automatically maximized when launching new PDFs. I used devilspie to correct that. I now rely on an ugly workaround, which is OK for practical purposes.

---

### Post by Paddy Landau on 2023-12-05
> **vanadium said:**
> One of the issues is that Wayland is fragmenting. While tools for Xorg would work on any desktop, each Wayland compositor has its own set of protocols. …
That is disappointing indeed!

Thanks for the information. I'll have to add those to my notes and test them.

It's a bit depressing, really, as I don't have the time any more to look at these.

Oh well.

---

### Post by TheFu on 2023-12-05
Evince has become an abomination because it doesn't work with window decorations.  I want/need all windows to have a similar border like all the others, under the control of the WM, not the app. I'd like the title, buttons, colors, scrollbar, and resizing to all work the same across all windows, regardless of where they are running (I run about 80% of my GUI programs on remote systems).

Someone needs to tell the Wayland people - just because MS-Windows does it that way, it doesn't make it a good idea.

---

### Post by ajgreeny on 2023-12-05
> **TheFu said:**
> Evince has become an abomination because it doesn't work with window decorations.  I want/need all windows to have a similar border like all the others, under the control of the WM, not the app. I'd like the title, buttons, colors, scrollbar, and resizing to all work the same across all windows, regardless of where they are running (I run about 80% of my GUI programs on remote systems).

Someone needs to tell the Wayland people - just because MS-Windows does it that way, it doesn't make it a good idea.
I totally agree!

In fact I'd go further and say that many of the dedicated gnome applications have become abominations as far as their GUI is concerned, eg nautilus (files), gthumb, etc.

---

### Post by kiwi9 on 2024-04-07
I like KDE Plasma but dropped it for XFCE when I saw that only wayland would be supported with Plasma 6.   This has since been proven incorrect and I've been keeping an eye on functionality that might support my X11 activities.   There's a new tool, [kdotool]("https://github.com/jinliu/kdotool"), that handles the input and window management side using kwin scripts and dbus interfaces.  Also I prefer [dotool]("https://git.sr.ht/~geb/dotool/tree/HEAD/doc/dotool.1.scd") to ydotool. So I'll probably move to kde again and use wayland once 6 is stable and widely supported.



[COLOR=#000000][TABLE="class: cms_table_grid, width: 100%, align: center"]
[TR]
[TD]**X.Org tool**[/TD]
[TD]**Wayland equivalent**[/TD]
[/TR]
[TR]
[TD][FONT=&amp]xdotool [/FONT]&#8230;[FONT=&amp] --clearmodifiers[/FONT][/TD]
[TD]Unavailable[/TD]
[/TR]
[TR]
[TD][FONT=&amp]xdotool type [/FONT]*[pattern]*[/TD]
[TD][FONT=courier new]echo [pattern] | dotool[/FONT]
**Comments:**
[FONT=courier new]Your user needs to be in group, input[/FONT].[/TD]
[/TR]
[TR]
[TD][FONT=&amp]xdotool key [/FONT]*[key]*
E.g.
[FONT=&amp]xdotool key super+F1[/FONT][/TD]
[TD][COLOR=#000000][FONT=Verdana]echo key shift+1 x:exclam shift+k:2 | dotool[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD][FONT=&amp]xdotool search --pid=[/FONT]*[pid]*
[FONT=&amp]xdotool search --name [/FONT]*[name]*
[FONT=&amp]xdotool search --onlyvisible [/FONT]&#8230;[/TD]
[TD]kdotool search [name]
you could search names and check the pids with getwindowpid
onlyvisible is missing in kwin[/TD]
[/TR]
[TR]
[TD][FONT=&amp]xdotool getwindowfocus
xdotool getwindowfocus getwindowname
xdotool getactivewindow
xdotool windowfocus
xdotool windowraise
xdotool windowmove [/FONT]*[window ID][edge]*[FONT=&amp]% y[/FONT][/TD]
[TD]kdotool getactivewindow
kdotool getactivewindow getwindowname
windowstate can return above, below, skip_taskbar, skip_pager, fullscreen, shaded, demands_attention
windowactivate, windowraise and windowmove all work[/TD]
[/TR]
[TR]
[TD][FONT=&amp]wmctrl -d
wmctrl -i -a [/FONT]*[window ID]*[FONT=&amp]
wmctrl -i -r [/FONT]*[window ID]*[FONT=&amp] -b add,maximized_vert
wmctrl -i -r [/FONT]*[window ID]*[FONT=&amp] -b add,skip_taskbar
wmctrl -i -r [/FONT]*[window ID]*[FONT=&amp] -t [desktop][/FONT][/TD]
[TD]kwin is quite powerful allowing some of the functions directly and some from kdotool[/TD]
[/TR]
[TR]
[TD][FONT=&amp]devilspie2[/FONT][/TD]
[TD]kwin is quite powerful allowing some of the functions directly and some from kdotool.
  I was disappointed with devilspie's abilities compared to kwin but your use may be
different.[/TD]
[/TR]
[/TABLE]
[/COLOR]

---

### Post by Paddy Landau on 2024-04-08
@kiwi9 &#8212; Thank you for this. Do you think that these will work on non-KDE systems? Ubuntu uses GNOME.

---

