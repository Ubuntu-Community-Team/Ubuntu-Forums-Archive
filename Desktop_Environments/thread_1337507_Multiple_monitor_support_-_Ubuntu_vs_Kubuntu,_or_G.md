---
title: "Multiple monitor support - Ubuntu vs Kubuntu, or Gnome  vs KDS"
date: 2009-11-25
forum: Desktop Environments
---

### Post by alewis on 2009-11-25
Firtsly - I have asked this over in the kubuntu forum, but the forum traffic is low and I may await an answer , or even a response, for some time!

I installed Ubuntu 9.10 via wubi onto my PC. I use a dual monitor system, with an ATI 1950 card. Worked flawlessly. By default, the display was set to 1600x1200 and mirrored onto the second monitor. However, the system did understand that there are two outputs and two monitors, and it was a quick job to tick the multimonitor option.

Then someone mentioned that kde offered nicer/better/different visual effects, so I thought I'd give Kubuntu a whirl. Installed, as before I have a cloned desktop not dual screen. Ok, lets fire up the system gadget to enable dual monitor support, as opposed to to a clone desktop.

Ok, lets try and find the system config tool... Right, "identify monitors" results in a window with  DISPLAY 1  and DISPLAY 2  in it, on both screens, not exactly promising. Click on multiple monitors... and have a message that "this is for environments with two monitors where users wish to extend the desktop across both. You do not have this" or similar. And no way of tellng it different... even though it recognises there are two dvi ports and both are in use. K, lets try changing the resolution on one. Hmm, no go either, it changes it on both. And whats more, it doesnt change the desktop resolution, but creates a display window of that resolution, in which one can scroll the desktop around it, as though the desktop is still setto 1600x1200 and the display is set to 1280x1024.

K, lets rtfm. Oh,not good. It discusses an interface or display tool that is different to the one shipped. Whats missing is the "hardware" section. Ok, what about "multiple monitor" in the system handbook.. "<long local url>monitor.html missing" Oh great.

So.... any ideas how to enable multiple monitor support in Kubuntu/KDE, even though it works fine in Ubuntu/Gnome ?

---

### Post by Zorael on 2009-11-25
<edit: omitted>

I don't know what's up with that systemsettings module (Multiple Monitors). There seems to be a patch for it that OpenSUSE uses and that has only just recently been pushed upstream for 4.4. It could probably be backported by the Kubuntu devs, if they know people want it to be.

[https://bugs.kde.org/show_bug.cgi?id=180437](https://bugs.kde.org/show_bug.cgi?id=180437)
[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/403610](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/403610)
[https://bugzilla.novell.com/show_bug.cgi?id=468931](https://bugzilla.novell.com/show_bug.cgi?id=468931)
[http://kubuntuforums.net/forums/index.php?topic=3107874.msg205118#msg205118](http://kubuntuforums.net/forums/index.php?topic=3107874.msg205118#msg205118)

This is a defect. The workaround so far seems to be to use GNOME's tool (as the kubuntuforums post describes), or to manually use the xrandr command line tool.

edit: Or grab ARandR from the repos. It seems to be a GUI frontend to randr.
> [SIZE="4"]**Features**[/SIZE]
[list][*]Full controll over positioning (instead of plain "left of") with edge snapping
[*]Saving configurations as executable shell scripts (configurations can be loaded without using this program)
[*]Configuration files can be edited to include additional payload (like xsetwacom commands tablet PC users need when rotating), which is preserved when editing
[*]Metacity keybinding integration:
[list][*]Saved configurations can be bound to arbitrary keys via metacity's custom commands.
[*]Several layouts can be bound to one key; they are cycled through. (Useful for "rotate" buttons on tablet PCs.)[/list]
[*]Main widget separated from packaged application (to facilitate integration with existing solutions)[/list]

---

