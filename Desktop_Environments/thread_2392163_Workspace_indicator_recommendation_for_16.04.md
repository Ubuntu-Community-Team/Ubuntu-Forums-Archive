---
title: "Workspace indicator recommendation for 16.04"
date: 2018-05-17
forum: Desktop Environments
---

### Post by turbo2ltr on 2018-05-17
Linux desktop newb here. I bought a new desktop, came with Win10 pro.  Within a day of using windows 10 I was ready to throw it off the balcony. It's rage inducing. I've been using linux servers for years, maybe it's time to try a linux desktop.

So I had a program on my windows box that was essentially the same thing as workspaces in ubuntu. It had an indicator in the system tray that told me what workspace I was on.  I went looking for something similar for unity and the only thing I found was indicator-workspaces. It ran but it would crash if you clicked it.

The indicator in the launcher does not seem to update when using keyboard shortcuts to move between workspaces.  Additionally, my configuration is 4 wide x 1 high, so the 2x2 grid doesn't really match.

I found this, which looks perfect, but I haven't a clue how to install it.  [https://github.com/maho2nd/enhanced-ubuntu-workspace-indicator](https://github.com/maho2nd/enhanced-ubuntu-workspace-indicator)

Any help or recommendations for other packages would be awesome. Thanks!

So far I like ubuntu.  Though I have to say the inconsistencies with window focus when switching workspaces (Windows always kept track of windows z-order and which window had focus), and it not remembering window placements when opening programs might drive me to appreciate windows just a tiny bit.

---

### Post by dino99 on 2018-05-17
Unity is still used on 16.04, but development is abandoned now; gnome is the default DE on 18.04 (which LTS as 16.04)
Workspaces are dynamic and exposed in the topbar

---

### Post by deadflowr on 2018-05-17
> The indicator in the launcher does not seem to update when using keyboard shortcuts to move between workspaces. Additionally, my configuration is 4 wide x 1 high, so the 2x2 grid doesn't really match.
That's because it's just a picture.

---

### Post by turbo2ltr on 2018-05-17
> **deadflowr said:**
> That's because it's just a picture.
It changes when you use the menu to switch workspaces...but not when using the keyboard.

I guess 18 JUST went LTS because I just installed this a couple weeks ago and I chose 16.04 vs 18 because of the LTS..  I feel dirty upgrading a brand new install, but I don't have time to start from scratch again..

---

### Post by Dennis N on 2018-05-17
A workspace switcher and indicator for Ubuntu 18.04 (see attached image) is a Gnome extension. Number of workspaces by default is dynamic, meaning there is an empty workspace added to whatever number you are currently using, or workspaces can be configured to show a fixed number. To see hint of contents, you have to use the Activities Overview (where you can also switch between them).

---

### Post by deadflowr on 2018-05-17
> It changes when you use the menu to switch workspaces...but not when using the keyboard.

By picture I mean it's just a generic image (or set of images) and not a traditional workspace switcher.
It's not dynamic. It cannot be changed or extended beyond the default 2X2 it shows.
And cannot be manipulated within the switcher picture (you cannot move the image within the picture to another workspace in the picture)
And it does not show anything beyond a single perceived window on a single workspace.
It always show one, even when no windows are even open. 

All it's really there for is to invoke expo.
Left click to see the viewport overview left click again to close the overview.
(and right click to invoke direct moves to any of the particular workspaces you wish to go)


If the goal is to have a dynamic actually mostly functional workspace switcher then I'd suggest looking into other desktop environments.
Kubuntu, Xubuntu, Lubuntu, Ubuntu Mate, Gnome flashback ( and Gnome-shell with particular extensions, like what Dennis N posted)
all have or can have this feature. 
Unity (Ubuntu's desktop on 16.04) has forsaken this option.
You can consider unity to be the outlier in this case.

FWIW I'm not sure about trying out a seemingly dead project from github.
But you can if you want. User's choice.

---

### Post by mc4man on 2018-05-17
The expo launcher icon is hard-coded for 2x2 so no user side way to alter.
Here I've always used 4x1 (cube/rotate) so have altered that since 14.04.

Decided to make available for other 4x1 users, plus a few other simple enhancements
[https://launchpad.net/~mc3man/+archive/ubuntu/unityplus](https://launchpad.net/~mc3man/+archive/ubuntu/unityplus)

Edit: the layout is 
12
34

---

