---
title: "fluxbox tray strange behaviour"
date: 2011-08-28
forum: Desktop Environments
---

### Post by bitches_brew on 2011-08-28
hello

my fluxbox system tray behaves strange:

[http://fotofotki.pl/images/xcyh4o2udngynje4bww.png](http://fotofotki.pl/images/xcyh4o2udngynje4bww.png)

these white spaces occurs. Longer the session lasts, bigger the spaces are. This is realy annoying. What program can be responsible for that?

i use ubuntu 11.04

thanks

---

### Post by fsnk on 2012-02-09
I have this problem too. I haven't found a solution for it yet.

It's really annoying.

---

### Post by andrew.46 on 2012-02-10
Sounds a little odd, are you running 1.3.2?

```

andrew@skamandros~$ fluxbox -version
Fluxbox 1.3.2 : (c) 2001-2011 Fluxbox Team 

```

Interesting as well to see what you are both starting in $HOME/.fluxbox/startup ?

---

### Post by nanovella on 2012-02-18
Hello, 

I have the exact same problem. It seems that the tray becomes bigger every time it resumes from suspend.

Here is what I have in my startup file:

nm-applet &
touchpad-indicator &
xfce4-power-manager &
fbsetbg -l

Any ideas ?

Thanks.

---

### Post by Rodney9 on 2012-02-18
Fluxbox 1.3.1 is the latest in Synaptic.

Rodney

---

### Post by andrew.46 on 2012-02-21
> **Rodney9 said:**
> Fluxbox 1.3.1 is the latest in Synaptic.

Might be worth investigating an upgrade to latest version though to see if the problem persists. Changelog shows a lot of work:

```

Changes for 1.3.2

*11/10/22:
    * Bugfix: possible crash at SIGINT / exit (Mathias)
    FbTk/ImageImlib2.cc

*11/10/17:
    * Removed (obsolete) Gnome window manager hints (Mathias)
      Gnome.{cc,hh} fluxbox.cc main.cc configure.in src/Makefile.am
*11/10/15:
    * Cleaned master translation file from obsolete stuff (Thanks skizzhg)
      Marked obsolete entries as _OBSOLTE to help other translators to identify
      them. Also, removed entries which are meant for error reporting anyway.
      nls/C/Translation.m
    * Updated italian translation (Thanks skizzhg)
      nls/it_IT/Translation.m

*11/09/17:
    * Tons of changes all over the place (Pavel)
      RefCount, FbTk::Timer, const Signals, Documentation fixes etc

*11/09/11:
    * Compilefix: build without 'iconv' support (Thanks to Peter Korsgaard)

*11/09/10:
    * Bugfix: sync the copied config files to the disk before continuing to
      launch. This avoids possible race conditions, eg. under MacOSX (Mathias)
      main.cc

*11/09/01:
    * Relicense 'ostrich' theme (to please Debian / Ubuntu) (Sven)
    * Bugfix: Do not change workspaces when using NextWindow/PrevWindow in toolbar (Mathias)
      ToolFactory.cc

*11/08/26:
    * Mapping keysyms to keycodes after 'MappingNotify', closes #3386257 (Mathias)
      Keys.cc
    * Regrab ButtonMotionMask, needed for 'Move' events in .fluxbox/keys (Mathias)
      Keys.cc

*11/08/11:
    * Fixed using _NET_WM_ICON wrongly, (re)closes #1852693 (Mathias)
      Ewmh.cc
    * Updated 'bloe' and 'arch' styles to work without XPM support (Sven)

*11/05/16:
    * Fixed Textdialog and TooltipWindow style rendering bugs, added
      parentrelative labels (Thanks Nacitar Sevaht)
      TextDialog.cc TooltipWindow.cc

*11/05/10:
    * Use the new signal system exclusively (Pavel)
      In 2010 Henrik introduced a new signal/slot system as a replacement
      to the observer/subject code. That transition was never completed.
      Pavel cleaned up the missing parts, fixed some crashes related to
      restart() / shutdown of fluxbox.

*11/05/09:
    * Fix build system (Pavel)
      data/Makefile.am

*11/05/08:
    * Added check for CARDINAL via client patterns (Thanks to Nacitar Sevaht)
      ClientPattern.cc Ewmh.cc FbTk/FbWindow.{cc,hh} Focusable.hh Gnome.cc
      Screen.cc WinClient.hh Window.{cc,hh}

*11/04/27:
    * Fixed build system issues, tuned .gitignore (Thanks Pavel)

*11/04/25:
    * Bugfix: do not warp workspaces with only one workspace (Mathias)
      Screen.hh

*11/04/15:
    * Fixed some compiler warnings (Thanks Pavel)
      tests/testRectangleUtil.cc tests/texturetest.cc

*11/04/14:
    * Bugfix: crash on Sparc64, closes #3285968 (Thanks David Coppa)
      src/Screen.cc
    * Fixed typo on style 'MerleyKay', closes #3286430 (Thanks David Coppa)

*11/04/11:
    * Adjusted tips of 'fbsetbg' to current behavior (Thanks skizzhg)
      util/fbsetbg

*11/04/09:
    * Fixed some clang-compiler warnings (Thanks to Pavel)
      FbTk/Image.cc
    * Fixed VPATH builds (Thanks to Pavel)
      Makefile.am data/Makefile.am src/Makefile.am src/tests/Makefile.am
      util/update-fluxbox_configs.cc

*11/04/03:
    * Bugfix: correct calculation of height if container is rotated
      vertically, closes #3195728 (Thanks to Gediminas Liktaras)
      IconbarTool.cc

*11/04/02:
    * Fixed some typos in the manpages (Thanks to Pavel Labath)

*11/03/29:
    * fluxbox-generate_menu cleanups (Thanks slakmagic at gmail com)

*11/03/28:
    * Compile fix: gcc-4.6.x needs <cstdlib> for 'size_t' (Thanks Danial Diaz)
      FbTk/LayerItem.hh FbTk/MacroCommand.h FbTk/MultLayers.hh
    * Updated turkish translations (Thanks Mesutcan Kurt)
      nls/tr_TR/*

*11/03/23:
    * Compile fixes for Sunstudio12 (sunCC 5.1), cosmetics (Mathias)
    * Fix 'sstream' configure test (Mathias)
      configure.in

*11/03/19:
    * Bugfix: delete configmenu first at shutdown (Henrik)
      Screen.cc
    * Bugfix: reposition windows only if invisible (Mathias)
      Screen.cc
    * API cleanup (Mathias)
      ScreenPlacement.{cc,hh} MinOverlapPlacement.{cc,hh}
    * Reduced code deduplication (Mathias)
      RectangleUtil.hh Screen.{cc,hh}

*11/03/18:
    * Bugfix: crash when using ClientMenu after changing the client, closes #3210493 (Mathias)
      ClientMenu.cc
    * Bugfix: misordered Toolbarplacmenet strings, closes #3195721 (Mathias)
      Toolbar.cc
    * Compiler patting, closed #3204402, love for src/tests and manpages (Mathias)
      Screen.hh Window.hh ScreenPlacement.{cc,hh} configure.in
      src/tests/* doc/asciidoc/fluxbox.txt doc/asciidoc/startfluxbox.txt

*11/02/27:
    * removed (outdated) russian documentation (Thanks Slava Semushin)
      doc/ru/* configure.in

```

I do not use PPAs but perhaps this one might be worth looking at:

[https://launchpad.net/~fluxbox-maintainers/+archive/nightly](https://launchpad.net/~fluxbox-maintainers/+archive/nightly)

It is owned by Paul Tagliamonte who packages Fluxbox for Debian and I know from irc as a great guy :).

---

### Post by sickiwicki on 2012-04-18
Hi guys,

have you found a solution for this so far? I'm annoyed with this also. I use suspend a LOT (current uptime >6d) on my Lenovo X220 (Fedora 16 + fluxbox 1.3.2) and it results in the fluxbox systray despite having only 6 icons covering about 60% of the toolbar.. It's making the window list quite small and unreadable..:(

---

### Post by ColinTempler on 2013-01-29
It seems somebody opened a bug report in [launchpad]("https://bugs.launchpad.net/ubuntu/+source/fluxbox/+bug/930230").
I can confirm this happens also on debian unstable atm.
The solution is to restart fluxbox from its menu, the windows/apps will retain the current workspace.

---

