---
title: "XDG menu wierdness"
date: 2006-03-05
forum: Desktop Environments
---

### Post by barthel on 2006-03-05
While I'm pleased to find that Breezy is using the freedesktop.org spec, I'm encountering some odd issues on my system. I'd appreciate it if someone could help by correcting my understanding of the XDG menu draft or confirm that there is a bug (and whether I should report it as an Ubuntu, GNOME, or Freedesktop bug. )

**Issue 1: Desktop directories not appearing in the menu structure.**

Following the spec, I put .desktop files for locally installed programs in /usr/local/share/applications. As of today this directory contains:
[INDENT]gvim.desktop - no .desktop in package
Lux.desktop - a locally installed game
Nautilus-root.desktop - manually created to let me easily use Nautilus as root
penguin-command.desktop - no .desktop in package
timidity.desktop - no .desktop in package
tkpasman.desktop - locally installed with utility[/INDENT]

All of these appeared in the correct menus (based on their respective category strings) except gvim & tkpasman. They don't appear *anywhere*. Not even in "other". I've just spent a couple hours trying various tweaks and nothing made a difference. I was just about to *forcibly* add them via smeg, except that smeg shows them both under Accessories. :confused: 

Here are the current .desktops:
```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Name=GNOME Vi IMproved Text Editor
GenericName=Vi Text Editor
Comment=Edit text files
Exec=gvim %F
TryExec=
StartupNotify=true
Icon=vim
X-GNOME-DocPath=
Terminal=false
Categories=Application;Utility;TextEditor;

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=TkPasMan
GenericName=Password Manager
Comment=
Exec=tkpasman
TryExec=
Icon=password
X-GNOME-DocPath=
Terminal=false
StartupNotify=true
Categories=Application;Utility;

```

For what it's worth, these were copied over from my prior installation of Slackware and had been been working there. I've pulled out what little hair I have left and haven't been able to figure this out. Anyone?

**Issue 2: Submenus cause duplication of menu entries**

On this one, I've just done a lot of empirical testing and I think I know what the issue is. Here's the scenario:

OpenOffice. I don't use it that often, so I want to put all those icons in a submenu. (The "weight" of 7 very similar icons all in a group draws my eye away from the 5 key ones currently installed.) So I fired up Vim to edit my menu localizations in /etc/xdg/menus/applications-merged/trippant.menu.

Since there was no category tag I could use, I explicity included each desktop file in my new subdirectory. Then the fun began. Here are the variations. Please note that none of these changes touched /etc/xdg/menus/applications.menu--I'm following the draft guidelines by putting all my changes into a merge menu.

a) <Exclude> those files from the parent Office directory. Result: they appear in both "Office" and "Office/Open Office"
b) Add the <OnlyUnallocated/> tag. Result: The Open Office icons only appear in the "Office/Open Office" submenu. But all the other "Office" icons appear again under "Other". This is true whenever the <OnlyUnallocated/> tag is used whether <Exclude> tags are also used or not.
c) Reviewing the spec again, I note that you can't <Exclude> before you <Include>. On the off chance that there's a parsing order issue, I tried <Not> including the Open Office desktops instead of <Excluding> them. Result: they still appear in both "Office" and "Office/Open Office"


But it's the C) version that's the gives the jumpstart to my brain. Going back to scenario (a), this time I edited /etc/xdg/menus/application.menu: I moved <DefaultMergeDirs/> to the bottom of the menu specification. Voila! No duplication of icons anywher, no spurious appearances under "Other".

It is my opinion that the <DefaultMergeDirs/> tag is causing the contents of the merge directories to be processed before the "default" menus which follow. So even though I explicity excluded the items I moved to a new submenu, they were included again by virtue of the default menu rules. The <OnlyUnallocated/> tag, when used in a submenu, does not appears to be tag the .desktop files now appearing in the submenu as  allocated.

These are the possibilities as I see them:
a) The implementation of the XDG menus is broken, since <DefaultMergeDirs/> is not resulting in the merged menus overriding the defaults. But given that would require that the <DefaultMergeDirs/> tag behave differently from all the other merge tags, I don't think this is the case.
b) The sample .menu file is wrong. While we do want to read in legacy directories first to allow them to be overwritten, we have to put off reading the vendor, system, and user merge menus until after the defaults have been processed. So <DefaultMergeDirs/> should be the last tag before the final </Menu> tag. (I should also point out that this is the simpler fix, which gives the documented behavior without changing the codebase in any other way. It's also how the kde-applications.menu file is set up in kdelibs-data 4:3.5.1-0ubuntu0breezy1. Too bad I didn't spot that before I did all this work.... )

As regards to the <OnlyUnalloacted/> tag, I suspect that it's a blind spot in the specification itself, simply because it's only used for the "Other" menu and the preference for a flat menu structure as the default. Maybe I'm just interpreting the spec wrong, but think how much easier it would be to modify menus if we didn't have to explictly exclude items in submenus of the current branch.

Personally, I think it would be a better default behavior:
[INDENT]include all the .desktop files that match the inclusion categories
exclude any that match the exclusion categories
exclude any that are explicity excluded by filename
exclude any that already appear in a submenu of the current menu
include any that are explicitly included by filename--even if they appeared in a submenu[/INDENT]

At any rate, should I file relocationg <DefaultMergeDirs/> as a Dapper request, or should I try to push this up to the GNOME or FreeDesktop groups?

Thanks!

---

