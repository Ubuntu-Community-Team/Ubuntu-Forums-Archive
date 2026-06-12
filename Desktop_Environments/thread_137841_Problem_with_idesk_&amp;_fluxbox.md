---
title: "Problem with idesk &amp; fluxbox"
date: 2006-02-28
forum: Desktop Environments
---

### Post by justin.parker on 2006-02-28
Not entirely sure if this is the appropriate place for this, but I figured it would be worth a shot.  I'm currently in the process of building some simple kiosk machines for public workstations, and decided upon ubuntu + fluxbox + idesk as the development background.  Everything is working perfectly, except for one small problem.

When the wm loads, it loads idesk first, then it executes fluxbox.  Everything runs fine, all is well.  All continues to be well, assuming the user double clicks the icons, or uses the menu to navigate through the available applications.

However, it seems that idesk is crashing when a user (whether on purpose or not) attempts to drag the icons around the desktop.  I have both attempted to disable this feature and to leave it enabled, and it seems that neither of the options are working.  When the user attempts to drag the icon around the desktop, idesk immediately crashes and the process stops running.

Restart the process and everything once more is fine and functional...until the next user attempts to drag an icon around.  Same problem persists.  In my attempts to try to hunt down errors its throwing or reasons why it is crashing i have found almost nothing.  Nothing gets dumped into /var/log/messages or anything else in the logs.

Suggestions?  Anyone else run across this problem?  I'm using idesk 7.3-2 installed from apt-get along with fluxbox also installed from apt-get.  Any help would be greatly appreciated, I can't have this problem persisting when I push these machines to production.  Thanks in advance.

Justin

---

### Post by Xian on 2006-02-28
Well, I've heard of idesk crashing when Nautilus is being run but this dragging icon buisness is new to me. I've been working on the Fluxbox ubuntu-wiki and just haven't gotten around to doing a section on idesk, but my best advice would be to lock down those icons if that is what indeed is causing the problem. You said you attempted to disable the feature but didn't give any specifics. What does your .ideskrc file contain?

You need to edit your /home/<username>/.ideskrc file and be sure the option below is enabled:

Locked: true

Here is an example .ideskrc file (without the lock enabled):

```
table Config
FontName: verdana
FontSize: 12
FontColor: #ffffff
Locked: false
Transparency: 100
Shadow: true
ShadowColor: #000000
ShadowX: 1
ShadowY: 2
Bold: false
ClickDelay: 300
IconSnap: true
SnapWidth: 55
SnapHeight: 100
SnapOrigin: BottomLeft
SnapShadow: true
SnapShadowTrans: 200
CaptionOnHover: false
end

table Actions
Lock: control right doubleClk
Reload: middle doubleClk
Drag: left hold
EndDrag: left singleClk
Execute[0]: left doubleClk
Execute[1]: right doubleClk
end
```

---

