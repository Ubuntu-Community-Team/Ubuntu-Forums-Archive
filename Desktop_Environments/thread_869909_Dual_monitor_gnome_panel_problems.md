---
title: "Dual monitor gnome panel problems"
date: 2008-07-25
forum: Desktop Environments
---

### Post by AAASmith on 2008-07-25
I got dual monitors and compiz working using the restricted nvidia drivers and nvidia-settings.  I'm using the "Separate X screen" configuration with Xinerama disabled.  This gives me two distinct desktops with two sets of workspaces, two rotating cubes, etc. instead of just stretching the desktop across both monitors.

Most things work fine except that some applications can't seem to find the right panel.  Or any panel.  The workspace switcher on the right monitor works as it should.  The other one only displays two workspaces.  When I try to raise the number to four on the left monitor, the changes take effect on the right monitor instead.

Also, applications that should have an icon in the panel show up in the desktop instead.  E.g. the software update notifier and Pidgin both end up with icons in windows outside of the panel.  In the attached screenshot, the graphic circled in red is supposed to be in the notification area in the upper right, but it has its own window instead.

Finally, for some reason, menus are very slow on the right monitor.  E.g when I click "Applications" on the top panel or when I right click in Firefox, there's a really noticeable delay before the menu pops up.

---

### Post by naszaklasa on 2008-07-25
> **AAASmith said:**
> 
Finally, for some reason, menus are very slow on the right monitor.  E.g when I click "Applications" on the top panel or when I right click in Firefox, there's a really noticeable delay before the menu pops up.

I had exactly same problem yesterday. This [http://ubuntuforums.org/showthread.php?t=536045&highlight=compiz+slow+menus&page=5](http://ubuntuforums.org/showthread.php?t=536045&highlight=compiz+slow+menus&page=5) fixed the issue.

---

