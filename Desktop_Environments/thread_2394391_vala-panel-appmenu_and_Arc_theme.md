---
title: "vala-panel-appmenu and Arc theme"
date: 2018-06-15
forum: Desktop Environments
---

### Post by notesetter on 2018-06-15
I'm running Ubuntu Mate 1804, favoring a customization of the 'Cupertino' (Mac) layout, and I've settled on the ever-challenging [Arc]("https://github.com/NicoHood/arc-theme") theme (because it really is quite nice). As you all know, Mate upgraded the global panel menu to [vala-panel-appmenu]("https://github.com/rilian-la-te/vala-panel-appmenu") for 1804, and it's quite an improvement (still a few nagging issues). But since Arc combines a light theme with a dark panel, the panel menus are all out of whack:

[IMG]http://www.davidstocker.notesettersinc.com/images/arc-vala-appmenu.png[/IMG]

I endeavor to:

[LIST]
Change the text color of the items on the Vala Appmenu to black or dark grey to increase contrast and readability, or
[/LIST]
[LIST]
Make the menu background match the panel background, leaving the menu text color as is.
[/LIST]

Has anyone already solved this? I'm down for working this out with some help. As it is, I'm not even sure which set of files to manipulate (Arc/gnome-shell, Arc/metacity-1, Arc/gtk-2.0, Arc/gtk-3.0).

It would be nice to get a definitive answer on this and put it out for the community.

TIA,
David

---

### Post by cruzer001 on 2018-06-15
Hello

I do not have it installed so I did a quick read on it.  For Mate I would look at gtk3.  It has a configuration file that may help.  Have a look at it.

~/.config/gtk-3.0/

I would also look for a /gtk.css file, if not for Vala then for Arc.  Thats where I make similar changes in themes color and text.  

Do you have dconf_editor installed?  Not sure where it would show up in the editor or what it will offer, but worth a look for both vala and arc.

WIA,
c

---

### Post by notesetter on 2018-06-16
Hi,

I'll check these places and mess around with them a little. If I hit on a solution, I'll post revision on the Arc Theme maintainer's GitHub and link it here.

Thanks!

---

