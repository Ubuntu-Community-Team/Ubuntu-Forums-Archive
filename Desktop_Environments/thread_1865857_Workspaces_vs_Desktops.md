---
title: "Workspaces vs Desktops"
date: 2011-10-20
forum: Desktop Environments
---

### Post by james@finnall.net on 2011-10-20
I have been searching for an answer to understand the difference between workspaces and virtual desktops.  Can anybody explain easily or a link to a discussion that does explain?

I am using 11.10 and with CompizConfig settings I have set up 3 horizontal and 3 vertical workspaces with 1 virtual desktop.  That provides 9 workspaces.   I then go back and change the virtual desktops to 9.  From what I can tell there is no difference.  Should I now have 81 workspaces?  Switching to expo mode still only shows 9 workspaces.

The popup hints in CompizConfig settings use different terminology but allow the settings independent of the other.  So it would appear they are not the same thing.  But if all I can switch are workspaces, then how do I change virtual desktops?

Before Unity, to my knowledge all we had were workspaces and/or desktops (the same thing) was a choice in terminology.  But now it looks like they are something different from each other.   If they remain essentially the same thing even in Unity, please explain the 3 control settings in CompizConfig settings.

Thank you.

---

### Post by crdlb on 2011-10-20
Yes, with 9 virtual desktops containing 9 viewports, you have a total of 81 workspaces, but there's no way to actually use them since compiz's plugins only work with viewports within the first (and usually only) virtual desktop. So, that number of desktops setting is only there because compiz's core happens to support virtual desktops even though none of the plugins do.

The main practical difference between the two implementations is that a window can be placed so that part of it is in multiple viewports. In theory, a window manager could also let you pan around with the viewport, but compiz only lets you move in screen-sized increments like traditional desktops.

GNOME Shell seems to get along fine with virtual desktops, but I guess compiz must get some benefit from using viewports.

---

### Post by james@finnall.net on 2011-10-21
Well, that would explain my problems trying to use the third setting on virtual desktops.   I have found that increasing the setting beyond the default of 1 actually causes problems.  Programs are unable to identify their workspace correctly and when you try move it to another workspace they disappear.  :(

I think it also helps with terminology as well.   CompizConfig refers to "viewports" and I used that option to setup my hot keys to switch viewports.   But apps still refer to them as "workspaces" on the menu.  So then viewports = workspaces.  

Thanks, James

---

