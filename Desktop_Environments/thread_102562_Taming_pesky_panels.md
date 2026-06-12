---
title: "Taming pesky panels?"
date: 2005-12-12
forum: Desktop Environments
---

### Post by runlevel0 on 2005-12-12
I have configured my desktop to use 4 panels.

I set the configuration using [color=#009900]Ubuntu>System Tools>Config editor[/color]
in the [color=#009900]apps>panel>toplevels[/color] section, setting the XY coordinates by hand.

But sometimes the panels seem to think for their own and place themselves on weird places... 

I know there is a config file anywhere in the system, but I can't figure out how it's called (I'm a KDE guy). My idea is to chmod the file to read-only, so that it can't be changed by applications.

What file shall I edit?


TIA

---

### Post by runlevel0 on 2005-12-25
[QUOTE=runlevel0]I have configured my desktop to use 4 panels.
[/QUOTE]

There was an even better solution which eliminted the pesky panel problem definitively: Instead of grepping my whole HD to see where the heck Gnome hides it's secret config files [1]  I took the shorter approach and formatted the hard disk and installed Kubuntu. 

I still ignore why nobody knows where the config files are, googling wasn't of help either. Yes, I can RTFM, but analyzing the source code to find out where Gnome hides the panel configuration is something I'm not in the mood to do, and it seems that people are not specially interested in silly things like bothering where the configuration files of their software is (Perhaps executing regedit.exe?).

So that's what took us so long, getting to a point where nobody knows how to set up stuff w/o a f...n wizard :P

At least in KDE I know that all the important stuff is in .kde... And nope, what I xerach for is not in the 2-3 .gnome* directories in my Home.

---

