---
title: "my panel applets are not cooperating &gt;:("
date: 2010-04-16
forum: Desktop Environments
---

### Post by butterbridge on 2010-04-16
I am running ubuntu 10.04 beta 2 on my netbook so screen size is a precious commodity (especially the vertical screen height), so I tried to shift my panel to the left side like I used to do with the Mac OS dock.  The panel applets behave terribly and the system scheme is wonky when the panel is set to right or left (as shown with left panel in picture).   --For example, the indicator applet which shows battery, volume, email, rhythmbox, etc, doesnt rotate with the panel and is cut off.  The indicator applet session is also not rotated and cut off.  The button window switcher has small buttons and retains the system background, as does the menu (both on right panel).
I could set the background color different or completely transparent, but these applets retain the system background on their own

I hope it is a bug in the beta and won't be an issue in the stable release, but it is still proving to be annoying and I was wondering if anyone has any ideas about how to fix the problems.  I know some of these issues are minor but I am trying to optimize my available screen space and it would be nice if it could fit the theme as well.

---

### Post by butterbridge on 2010-04-20
No luck in my fiddling around, I don't suppose anyone has any ideas?

---

### Post by shazbut on 2010-04-20
It's a longstanding issue in gnome, see the bug reports:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/43066]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/43066")
[https://bugzilla.gnome.org/show_bug.cgi?id=86382]("https://bugzilla.gnome.org/show_bug.cgi?id=86382")

I don't see it being fixed until gnome 3.0, which is a complete redesign.

Other options are to install one of the docks (awn/docky) and remove or hide the panel(s).  This isn't something I've done before, as I don't really like the concept of docks.

---

### Post by fabounet on 2010-04-20
you can install Cairo-Dock and remove your gnome-panels, it has a lot of nice themes and applets, you come out better off !

---

### Post by mcduck on 2010-04-20
Some of the applets simply don't work well in vertical panels. To be honest, I don't think there's even an easy way how some of them could possibly work with vertical space instead of horizontal.

If possible, you can work around that by having one horizontal panel and putting all the applets that don't work on vertical panels there. All the launchers and such applets work just fine on vertical panels.

What comes to the ugly theme, the problem is your GTK theme that defines a background image for panels & panel applets. PAnel backgrounds set that way can't be scaled or rotated, while backgrounds set directly from the panel itself can. The solution to this is to edit your GTK theme and remove all panel theming from it (if you are lucky your theme has a separate panel.rc, in that case you can simply rename that to get rid of panel theming). Once that's done you can set the panel background image you want directly from the panel's options, and then use gconf-editor to enable rotation (and scaling) of the background.

Honestly, I really hate the recent habit of adding panel backgrounds in GTK themes, that simply fails to work for anything else than horizontal  panels that have exactly the width the theme's creator used. If the panel backgrounds were distributed as separate images instead you could just drag&drop them to the panel to set them as panel background, and the panel would be able to scale & rotate the images when necessary to fit your panel's size and orientation...

---

