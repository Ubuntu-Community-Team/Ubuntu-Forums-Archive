---
title: "Global menu problems"
date: 2009-03-08
forum: General Help
---

### Post by ChrisCarmichael on 2009-03-08
OK so i have installed the globalmenu applet before and had it working in the past however it will not work now. This is on a new installation of Hardy. 

It says

"Global Menu Plugin is not enabled on this desktop. Enable the plugin from the preferences dialog in the right-click menu."

Ok so i have checked the box, and unchecked it, logged in and out multiple times and restarted my computer a  few times installed it and reinstalled it. Nothing will get it to work.

Any help?

---

### Post by PhaeZee5 on 2009-03-19
bump, exact same issue, using hardy.

---

### Post by dudleydog on 2009-07-31
With the 0.7.5 version I'm getting a pop-up "hint" from globalmenu every time the desktop starts and stops, even though it's working fine :-P,  but on a fast system it comes and goes too quickly to read.

In order for the old Hardy version of GNOME to discover the module,  you may recall that following installation you must manually add a line to ~/.gnomerc like this:

export GTK_MODULES=globalmenu-gnome

After logging out and back in so the module can load, if it's not running as expected then double check it's active. For the benefit of anyone who never did this in the first place, as mentioned above you right click on the globalmenu portion of the GNOME panel to which you've added it, select Properties, and make sure the box is checked to actually activate it. (It's just another panel applet from the panel's perspective.)

If you installed using a package manager it will have all its dependencies, but I did see a situation on one of my installations where one of the libraries it depends upon was missing and globalmenu failed quietly until the missing library dpkg was restored (the details showed up in the logs when I ran dmesg, just had no complaints on screen).

---

