---
title: "Config Xfce Workspaces"
date: 2014-05-18
forum: Desktop Environments
---

### Post by Kurt_Alan on 2014-05-18
**[COLOR="#000000"][/COLOR][SIZE=5][/SIZE]**

i'm previewing a "live" version of Xubuntu 14.04.  If I can get Workspaces and Panels configured  robustly, as in Gnome 2.0, I just might have a fallback DE besides Unity.

However, Workspaces are a "no go."  

I opened Settings, selected my number of spaces and named them  Then I went to the Margins tab.  The explanation: "Margins are areas on the edges of the screen where no windows will be placed."  I don't know what that means. No windows or no workspaces? (A workspace is a small window). Anyway, assuming that I wanted my workspaces to show on a bottom panel, I marked zero for all sides and 5 for the bottom.

But where are my Workspaces? They are nowhere to be found.  Do I first have to create a Panel??

---

### Post by Dennis N on 2014-05-18
Workspaces are the same as desktops. The workspace switcher is also known as desktop pager. Each Workspace (Desktop) can have a margin reserved.

---

### Post by Kurt_Alan on 2014-05-18
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**

Yes, but what is a Margin? Can you give an example?  Meanwhile, I've set up a second panel, configured that, and have all my other workspace configs set: name, number, etc.

Gnome 2 workspace properties are the same as for Xcfe except for Margins.  Gnome 2 did not have Margins.

---

### Post by Kurt_Alan on 2014-05-19
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**

I still don't know what Margins are but no diff.  For the main problem, I solved it.  If you config Workspaces in Settings, those Workspaces will default to the default Panel which is Panel zero.  They are difficult to see unless you do further config.  

Solved.

---

### Post by ka55o5 on 2014-05-19
> **Kurt_Alan said:**
> Yes, but what is a Margin?> I am not sure if this is what you want, but you can tell Xubuntu to use an area of the workspace. Menu -> Settings -> Setting Manager -> Workspaces will show margins on the right side. 

The numbers around the square are the distance from the edge to use for the workspace. By changing those, you can force the applications to not go outside the visible area. 

You can still manually move windows outside the margins, but opening windows and maximising applications will stay in the margin set.```
http://askubuntu.com/a/43031/75115
```

P.S.
> **Kurt_Alan said:**
> No windows or no workspaces? (A workspace is a small window).
^^ As, in: an application, the Firefox (application) window.

---

