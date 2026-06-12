---
title: "Secrets of the Launchers"
date: 2010-11-21
forum: Desktop Environments
---

### Post by uriel1998 on 2010-11-21
I just switched my WM to Openbox, so this suddenly became a LOT more relevant to me.  However, the discrepancies between the open desktop standard and the "Debian/Gnome/Ubuntu" start menu can cause a lot of problems and confusion [(as seen in this thread)]("http://ubuntuforums.org/showthread.php?t=1621989").  I recently switched to Ubuntu from blackbox for windows, so I'm both a noob and an oldbie.  ::shrug::

So I'm going to put the information that I've had to figure out the hard way in one place.  I've probably mucked up the terminology, and may even have a major error somewhere, so additional comments are appreciated.

**Your Launchers/Shortcuts are hiding information from you.**

I'm not actually going to look at the start menu so much as the icons and applications that show up in it.  Sometimes apps will show up in Gnome-Do and Launchy (or a dock) that are nowhere to be found in the start menu.  Launchy put me on the right path to find the files.  They exist in (some or all of):

```

/usr/share/applications/
/usr/local/share/applications/
/usr/share/gdm/applications/
/usr/share/applications/kde/
~/.local/share/applications

```

These application launchers/shortcuts ( *.desktop files ) have a bunch of attributes, only some of which are available from the GUI.  Normally you see:  **Name**, **Description**, **Command**, **Comment**, and you can change the permissions, emblems, and icon.  Too bad that what you see in the GUI (Nautilus, for example) is not always the real file name.

I used [TuxCommander]("http://tuxcmd.sourceforge.net/") to actually get to the filenames themselves;  you can also use the Open dialog in Gedit to see the real filenames.  Because I'm an anal retentive kind of guy, I went through and renamed the files appropriately.  Then I opened the suckers up in a text editor.  These are the key values that you need to worry about (there's more values, but this is a "getting you running", not a reference manual.

```

#!/usr/bin/env xdg-open

[Desktop Entry]
Type=Application
Terminal=false
Name=DirSyncPro
Comment=DirSyncPro
Icon=/usr/share/icons/Faenza/apps/scalable/zen-icon.svg
Exec=bash /home/usr/scripts/dirsyncpro.sh
Categories=System;Utility;

```

Most of these are pretty straightforward.  There are two reasons why some of these don't show up in the main menu.  

Some launchers have the value **Hidden=true**.  Obviously, that hides it.  Delete that line.

The other thing is the lack of the **Categories** value.  You can find a full list of the values [here]("file:///home/steven/Downloads/desktop_categories.html").  It's a bit tedious, but suddenly everything shows up where you expect it.  (And pipe menus for configuring *box menus work a lot better too.)

There are a *lot* more values to poke around with, but this should answer the typical noob question of "where are my shortcuts"?   Lord knows *I *had that question...

---

### Post by uriel1998 on 2010-11-25
An additional bit, if you're using Openbox and want dynamically (and I mean dynamic, on-the-fly) reconstructions of your Ubuntu menu:

[obtap]("https://bbs.archlinux.org/viewtopic.php?id=107999")

I'd been looking for a program like this for about two weeks now;  it recreates your menu on the fly and is VERY configurable.  Two key things so you don't have to redo your menu from scratch:

In the example.config file (which I just used in place), add in all the locations where files might be *inside* the parentheses and remove the extra crunches, so it looks more like this:
```
locations(/home/USERNAME/.local/share/applications,/usr/share/applications,/usr/share/applications/kde4) # Locations.
```

Second, after compiling **but before running** obtap, add this to your existing menu.rc:

```
        <menu id="Ubuntu" label="apps" execute=
        "/home/USERNAME/Apps/obtap/bin/obtap -c /home/USERNAME/Apps/obtap/goodies/example.conf -t openboxpipe -o -"
    />

```

Hope that helps someone else!

---

### Post by akwala on 2010-11-28
> **uriel1998 said:**
> The other thing is the lack of the **Categories** value.  You can find a full list of the values [here]("file:///home/steven/Downloads/desktop_categories.html").
Thanks for the helpful explanation!

The link you provided to the Categories list seems to point to a local file. Can you provide a web URL or post the list itself?

---

### Post by uriel1998 on 2010-11-28
> **akwala said:**
> Thanks for the helpful explanation!

The link you provided to the Categories list seems to point to a local file. Can you provide a web URL or post the list itself?

Oh, crap.  That's what I get for having my locally-saved copy open at the same time as the online one I want to point to. 

The appropriate reference is at [http://standards.freedesktop.org/menu-spec/latest/apa.html](http://standards.freedesktop.org/menu-spec/latest/apa.html)

The list of possible categories gets quite long.  The program ObTap I mentioned works *great* for OpenBox, and lets you combine/omit categories on the fly as well.

---

