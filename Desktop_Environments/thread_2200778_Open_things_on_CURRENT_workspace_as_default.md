---
title: "Open things on CURRENT workspace as default?"
date: 2014-01-21
forum: Desktop Environments
---

### Post by Luxx on 2014-01-21
Is there a way to change the default behavior from opening everything on Workspace 1 to opening things on the current workspace? I can't have everything open on Workspace1. It clutters workspace1 and everything I'm working on gets lost. It totally undermines the whole reason I use multiple workspaces. 

I have found several threads in these forums and others that address similar issues, but not a single one that explains how to get apps, folders, etc to open on the current workspace by default.

It was working that way 2 days ago, what I have perceived as normal for years. I don't want to use keystrokes or assign apps to a certain workspace or eliminate my other workspaces. These are the suggestions I have found in all the other threads. I just want to get things back to normal. I have a lot of work to catch up on and my workflow is trashed with this workspace behavior.

Oh, it might be relevant that I'm on gnome-session-flashback, not Unity.

---

### Post by Luxx on 2014-01-21
Am I seriously the only person who has this problem in gnome-session-flashback? All over the internet people have this issue with Unity, but I'm not using Unity....and the suggestions from using virtual machines or another X session to getting rid of the other workspaces, assigning apps to a workspace (which doesn't work if you use the same apps for different tasks in different workspaces) and other nonsensical work-arounds have me a little nervous. Is there really no way to get things to open in the CURRENT workspace? I thought this was supposed to be the default behavior???

---

### Post by Bashing-om on 2014-01-21
Luxx; Hi !

In addition to using  gnome-session-flashback, what version are you using ?
I do not use gnome as my DE, but others do and can advise.

[INDENT][INDENT]my bit to push this along
[/INDENT][/INDENT]

---

### Post by deadflowr on 2014-01-21
Metacity or compiz?

I find compiz is too tweaked for unity on Ubuntu.
Metacity seems much better than compiz.
In regards of gnome-classic(or whatever the current name is.)

Though this is geared toward precise, it  might give you some help
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by buzzingrobot on 2014-01-21
> **Luxx said:**
> All over the internet people have this issue with Unity...?


Apps, windows, etc. open in Unity's current worspace. Apps *restore* to their native workspace.  This latter was configurable in Gnome 2, and is configurable in Mate (a right-clickable option in the window-list panel applet).  Does flashback have sonething similar?

if your setup was working to your liking up to 2 days ago, find out what happened then to change things, and reverse it?

---

### Post by Luxx on 2014-01-21
It was all fine in metacity until I realized I couldn't resize windows and I installed compiz again. Now I can't go back to that configuration without my windows misbehaving, can't type, can't open anything, have to reboot to do anything.

So I guess I'm stuck in compiz.... just had to reboot again testing that theory... seems like a solid theory at the moment.

---

### Post by Luxx on 2014-01-21
OK....
@Bashing-om: I am using gnome-session-flashback 1:3.6.2-0ubuntu15 in Ubuntu 13.10

@deadflowr: I uninstalled Unity months ago. I settled on Gnome Classic (gnome-session-flashback) after trying other desktop environments (Cinnamon, Mate, E17, Fluxbox, etc.)

@buzzingrobot: The familiar gnome classic behavior is windows (apps, folders, browsers, whatever) would open in the workspace you were in when you launched them (current workspace) and they stayed there unless you moved them. You could click and drag to another workspace, across the workspace wall. I wish I could figure out what happened and how to reverse it. I thought I had it straightened out, but nothing was quite the same. I've been trying to figure this out for 2-3 days now.

Noticing other strange behavior:
-If I go to another workspace the bottom panel disappears, but if I open something (everything opens in W1) and send it to another workspace and then switch to that workspace the bottom panel is there. 
-Sometimes when I try to open something in W2,3,4 it opens in W1, but it takes a while for it to show up. 
-Sometimes when I try to open something in W2,3,4 it opens in W1, but has the wrong R-click menu in the panel, as if it is part of the desktop (no minimize, maximize, always on top, move to another workspace).
- Windows lose their borders and blend into other windows and the top panel at random. If the top panel is involved "killall gnome-panel" fixes it, but if just windows are stuck together I have to reboot to get anything working.

---

### Post by Luxx on 2014-02-05
After switching to Gnome 3 with Tweak Tools plugins I am getting sudden restarts. I think my last couple of issues were related. I am suspecting Xorg issue.

---

### Post by deadflowr on 2014-02-05
> [COLOR=#000000]@deadflowr: I uninstalled Unity months ago. I settled on Gnome Classic (gnome-session-flashback) after trying other desktop environments (Cinnamon, Mate, E17, Fluxbox, etc.)[/COLOR]

Never thought you had unity.
I just stated that compiz on Ubuntu seems to be tweaked to run unity first.
Desktops like classic seem to be more secondary priority.
So functions might not be as up to par as other distros using compiz.

Anyway, what tweak have you installed on gnome-shell?

---

### Post by buzzingrobot on 2014-02-10
> **Luxx said:**
> "...Tweak Tools plugins..."

If those are Gnome Shell extensions, disable them one at a time, logging out and in, and see if the fault persists.

---

### Post by Luxx on 2014-02-17
I'm getting similar strange behavior with every configuration I try. I tired not using the gnome-tweak-tools extension, using one tweak at a time (they are all part of the extension, not really separate plug-ins), using the other versions of Gnome3 with and without either of the classic shells.

---

