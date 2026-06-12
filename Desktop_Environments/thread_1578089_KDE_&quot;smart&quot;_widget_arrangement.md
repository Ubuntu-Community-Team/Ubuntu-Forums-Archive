---
title: "KDE &quot;smart&quot; widget arrangement"
date: 2010-09-19
forum: Desktop Environments
---

### Post by Dr. Strange on 2010-09-19
Apologies in advance if this is a little brusque; this problem has driven me round the bend and I'm about ready to break something.

Kubuntu 10.04 x86. I've got a working triple monitor arrangement, separate X displays tied together via xinerama, which is all well and good (within the limits of xinerama, anyway; I long for the day when spanning desktop space, multiple monitors on multiple adapters, and X compositing can all live in harmony...) except for how KDE handles widgets. Love KDE, haven't had a second thought since switching from Gnome earlier this year, except for this one reach-for-the-shotgun issue.

I like to have whatever I'm working on presently on my center monitor, my e-mail open on my right monitor, and various apps (torrent client, IM client, and a sort of 'status display' of arranged desktop widgets) on the left. KDE, on the other hand, does not like things this way.

KDE, it appears, has pretensions at being a GUI designer; it won't let me arrange widgets on my desktop the way I want to position them. If I put one in the top left corner, it'll snap into place. OK, fine; if I put another widget right below that first one, it automatically indents both of them, usually one in further than the other. Adding additional widgets to the arrangement usually but not always causes KDE to keep indenting - it's not stair-step bad, but it's obvious things don't line up which makes it visually distracting. It seemingly-randomly decides that I can't put a widget in a particular location on the screen and snaps it back to the size and location it was in when it first appeared on the screen (or before I moved it, if it was already there). It's not an overlap-detection problem; sometimes it's perfectly OK with me overlapping widgets, sometimes it won't even allow widgets to be within some apparently-randomly-chosen number of pixels of one or more of the widgets already on-screen. Sometimes it'll regard an aligned cluster of widgets as a single entity and snap to edges... with no rhyme or reason as to which clusters and which edges. When working with widgets in close proximity to each other, the 'edge-bars' that contain the buttons with which one can drag and manipulate the widgets; again, with little-to-no discernible pattern, sometimes they appear over the widget next to it, sometimes underneath the widget next to it (making the edge-bar completely useless), sometimes clicking the widget brings its edge-bar to the foreground, sometimes the widget needs to be dragged to a different part of the desktop or a different monitor then re-positioned in the cluster for the edge-bar to be in the foreground, sometimes the widget has to be removed and re-added to get the edge-bar into the foreground. When I rebooted just now, my widgets were randomly scattered across the desktop, despite having had "Lock Widgets" turned on throughout (since a few days ago, actually; the last time I had to re-re-re-rearrange things).

Basically, from what I can tell from several months of observation, KDE has some sort of automatic widget arranging 'feature' which a) doesn't work properly and b) has no bloody off switch. All this makes what should be the simple, five-minute task of resizing and lining up some widgets by hand into an hour-long test of the elasticity of my vascular system. I'm fine with there being new or experimental or even buggy features in my GUI... so long as I can **turn them off when I need to**.

I've done the requisite googling and have come up empty. I've looked everywhere in the GUI I can think of, but no luck. I don't yet know enough about KDE to know where to look in the conf files to hack around it by hand. Could someone please tell me how to dike out or simply turn off this blitheringly-stupid widget auto-positioning drunken &*#^$*@#%$^&% wart so that I, the human, can put things where I want them on the screen?

It's also baffling that I can only resize a Plasma widget up and away from its edge-bar when most every other window in most every other environment I've ever seen, including KDE, will let you resize by dragging any border in any direction. Big. Step. Backward. If anybody knows a way to fix this I would be most interested in hearing it, but I'll make do if given a way to turn off what I've come to think of as KDE's "layout critic mode".

Thank you, and, again, apologies for any bile that may have got on you whilst reading.

---

### Post by Dr. Strange on 2010-09-29
Essentially solved: Changing the Desktop Activity (right-click desktop -> Desktop Activity Settings -> Activity -> Type) from Desktop to Folder View makes the desktop work like that of Windows or MacOS; the desktop shows the contents of the /home/$USERNAME/Desktop directory (or whichever path is chosen). This also turns on many new options in the desktop right-click menu such as creating new files and aligning icons to the grid.

I can now position widgets however I want to the pixel while simultaneously forcing icons to align to grid and/or lock in place as desired. Nothing interferes with where I place and size objects. So, the issue proper is resolved (icons don't recognize widget borders, which is a potential problem but not a huge one). 

I would, however, like to know if there's any way at all to configure the snap and align properties (whatever they are) of the default "Desktop" Desktop Activity setting.

---

### Post by ankspo71 on 2010-10-08
> **Dr. Strange said:**
> 
I would, however, like to know if there's any way at all to configure the snap and align properties (whatever they are) of the default "Desktop" Desktop Activity setting.

I think I found what you are looking for. Go to System Settings > Window Behavior > Window Behavior (again), and then choose the Moving (tab). Here you can customize the "Snap Zones". The path I gave you is for KDE 4.5.1 which may be a little different than earlier versions.

Hope this helps

---

### Post by Dr. Strange on 2010-11-15
> **ankspo71 said:**
> I think I found what you are looking for. Go to System Settings > Window Behavior > Window Behavior (again), and then choose the Moving (tab). Here you can customize the "Snap Zones". The path I gave you is for KDE 4.5.1 which may be a little different than earlier versions.
Hope this helps

Thanks for your reply. Whichever version of KDE it is that Kubuntu 10.04 is running as of today, it keeps the snap behaviors in the same place. However, this appears to affect only windows, not Plasma widgets.

PS: I'm certain it's not a glitch; Kubuntu 10.04 on my Dell Mini 9 - which is gangbusters in all other ways - does the exact same thing as this (extensively frankensteined) Gateway E4100. The only computer I've got with a greater degree of hardware difference has a half-eaten fruit logo. Someone, who I'd like to shake warmly by the neck, clearly intended things to work this way.

---

