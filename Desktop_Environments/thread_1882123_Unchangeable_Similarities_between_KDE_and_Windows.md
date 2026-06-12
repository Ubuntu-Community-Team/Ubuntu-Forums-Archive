---
title: "*Unchangeable* Similarities between KDE and Windows"
date: 2011-11-16
forum: Desktop Environments
---

### Post by Lachlan_M on 2011-11-16
I had a specific question about GNOME/KDE differences that a forum search did not resolve.

When I've used Linux in the past, I've typically used GNOME (2.x), because I found it more Mac-like, while KDE seemed too Windows-like.  But GNOME 3.0 and Unity seem to have moved closer to Windows, with a more keyboard- and text-based paradigm rather than a mouse- and icon-based one, focusing on instant searches and such instead of menus and folders.

I realize that these changes are taking place in all major desktop operating systems.  (They're why I moved from XP to OS X and not to Vista, but even OS X is considerably less visual than the Classic Mac OS was.)  I don't mind as long as I can make my desktop environment work the way I want it to.  Unfortunately, GNOME 3.0 and Unity won't really let me do that at this stage in their development.

So now I'm looking at KDE again, because it's more customizable.  The whole reason I started using GNOME was because KDE seemed Windowsy, but I'm starting to wonder to what extent that's actually true.  A lot of the commonly-cited similarities between KDE and Windows---like having a single panel on the bottom---only relate to the default settings, which can be changed.

So my question is this: **What characteristics are present in both KDE (or its apps) and Windows, but not in other desktop environments (especially GNOME and Unity), and which cannot (or cannot easily) be changed by the user?**

So far I have these:

• KDE requires users to apply system settings explicitly, while GNOME has them take effect immediately.
• Some applications, like Chrome, are reluctant to put their close/maximize/minimize buttons on the left side of the title bar.
• Some applications are reluctant to use a single menu bar add-on.
• Dialog boxes usually have Yes-No-Cancel instead of No---Cancel-Yes.

Does anyone know of anything else?

---

### Post by Copper Bezel on 2011-11-16
I think it's largely the aesthetics, and some things that, as you say, apply more to Gnome 2 than Gnome 3. For instance, Gnome 2 was more modular, but Gnome 3 is actually less so, KDE included desktop indexing and search as a core functionality, but Gnome 3 does, too, and so on. 

For things you can't really change directly and are still relevant in comparing the current KDE and Gnome, KDE's bundled apps' UIs seem cluttered to a Gnome user, with a lot of Windows-y side panes and less whitespace in general, and I imagine that's a big part of the impression. 

I'm not certain I follow the premises, though.

[QUOTE=Lachlan_M]But GNOME 3.0 and Unity seem to have moved closer to Windows, with a more keyboard- and text-based paradigm rather than a mouse- and icon-based one, focusing on instant searches and such instead of menus and folders.[/QUOTE]

Are you talking specifically about Gnome Shell and Unity, or the Gnome 3 apps themselves? There are still other alternatives to the two shells - Cairo Dock, for instance, now installs a separate session that uses Compiz as the window manager and provides the dock and systray.

---

### Post by Lachlan_M on 2011-11-17
[quote=Copper Bezel]I think it's largely the aesthetics, and some things that, as you say, apply more to Gnome 2 than Gnome 3. For instance, Gnome 2 was more modular, but Gnome 3 is actually less so, KDE included desktop indexing and search as a core functionality, but Gnome 3 does, too, and so on. 

For things you can't really change directly and are still relevant in comparing the current KDE and Gnome, KDE's bundled apps' UIs seem cluttered to a Gnome user, with a lot of Windows-y side panes and less whitespace in general, and I imagine that's a big part of the impression. 

I'm not certain I follow the premises, though.[/quote]

No, that's actually very helpful: KDE apps are sometimes more cluttered.

I can't really blame you for not being able to follow this.  It does deal mostly with my personal impressions, and maybe this thread is just another example of me needlessly rambling.  Basically, I'm just trying to figure out to what extent KDE's Windows-like reputation is due to the way KDE actually works, as opposed to the way it's set up out of the box.


[quote=Copper Bezel]Are you talking specifically about Gnome Shell and Unity, or the Gnome 3 apps themselves? There are still other alternatives to the two shells - Cairo Dock, for instance, now installs a separate session that uses Compiz as the window manager and provides the dock and systray.[/quote]

I meant the shells.  I wasn't really aware that they were replaceable, though in retrospect the fact that there are *two of them* should've made it obvious. :oops: :rolleyes: I guess coming from Windows and OS X I still haven't grasped the difference between shells, desktop environments, window managers, and windowing systems.

I might be able to find a way to make GNOME work for me, then, if I can find the right shell.  So thank you.  :)

---

### Post by Copper Bezel on 2011-11-17
Cool - I'm glad that helped a little. = )

Yeah, the distinctions between all of those layers are severely muddled. Basically, the desktop environment is just a collection of apps running under a particular window manager, but the DE itself can be highly modular, with the ability to switch out any and all applications and / or the window manager itself, or tightly integrated in such a way that that isn't possible. So the distinctions between those layers and whether or not they really exist depends on the desktop environment.

Until Gnome Shell and Unity came along, the system panels and such were just applications being drawn like any other and managed by whatever window manager the user ran to composite them, and that's still true in KDE (so you can, for instance, run Unity's Compiz window manager over KDE without breaking anything.) Under Shell and Unity, the panels are drawn directly by the window manager and exist as plugins for or elements of that WM (which is, incidentally, how Windows does it - the same process that composites the screen provides the "SuperBar.") The drawback is that the tight integration between the shell, window manager, and core apps makes switching things out a little more complicated - but for the moment, at least, Gnome 3 can still be managed with Compiz as the window manager (with the Unity plugin disabled) and a third-party panel or dock arrangement.

---

