---
title: "I would quite like my desktop background to be an active terminal"
date: 2012-05-17
forum: Desktop Environments
---

### Post by J-E-N-O-V-A on 2012-05-17
I was wondering whether this is ever likely to happen?

---

### Post by David Andersson on 2012-05-17
By default in Ubuntu, the desktop surface is controlled by a Gnome-program. It controls what to show and what happens when you left-click or right-click. The X11-window system allows any program to be run in the "root window", but you have to tell Gnome to give it up. There are instructions on the web how to run a video, a terminal, or a screensaver as a wallpaper, but I don't know if they apply to recent versions of Ubuntu or Gnome.

If you find no how-to that neuters Gnome in your current Ubuntu, there is a Screenlet that may do what you want. Install *screenlets* and start it. Click *Get more screenlets*, search for *terminal* (or go to section "T"), go to *Terminal* by *spdf*, download, unpack the .tar.gz-file and extract the *Terminal* folder in your *~/.screenlets* folder (that is, you'll now have a ~/.screenlets/Terminal folder). Search for Terminal in *Screenlet Manager* and *Launch/Add* it. In the Terminal, *right-click>Properties>Options* and set *Opacity*, *Keep below*, and *Sizing>Border Width* as you wish. (Disclaimer: I have not tested this in Ubuntu.)

---

### Post by mcduck on 2012-05-18
There is rather easy and simple solution, at least as long as you are rtunning nomral Unity session (or otherwise using Copmpoiz as your window manager).

You can simply use the "Window Rules" -plkugin to set any terminal window you want to stary below other windows, stick to the desktop, ignore tasklist/pager, never minimize or hide etc....

...and then exclude the same terminal in the Window Borders-plugin to get rid of the window borders for it.

If you want to use the same terminal emulator with normal windopws as well, at least Gnome-terminal allows you to create separate profiles, so you could for example make a new profuile for the desktop terminal and set it to sue a fixed title, which you can then use in CCSM to match to that windoe only instead of all Gnome-terminal windows.

---

### Post by duracella on 2012-05-18
Theese articles might help:

[# link1]("http://maketecheasier.com/terminal-as-transparent-wallpaper-in-ubuntu/2008/05/21")
[# link2]("http://www.lucidlynx.com/how-to-use-terminal-as-a-desktop-background-in-ubuntu/")

though I have not tried any of them, but  I suppose it should work even if higher upgrade then lucid...

---

