---
title: "User switch applet and sytem menu not paying attention to gconf settings"
date: 2009-11-20
forum: Desktop Environments
---

### Post by epsilon72 on 2009-11-20
I'm trying to remove the suspend and hibernate options from the user switch session applet...but my changes in the gconf-editor aren't being paid attention to.

I go to apps-->gnome power manager-->general, and uncheck "can suspend" and "can hibernate", and nothing happens, even after logging out and logging back in.  If I remove the user switch session applet to get the shutdown option back in the system menu, hibernate still shows up in that shutdown menu too (but not suspend).  

Any ideas?  Changing those keys in Debian and Gentoo have the desired effect, but I can't figure out why it won't work in Ubuntu.

---

### Post by epsilon72 on 2009-11-20
bump?

---

### Post by epsilon72 on 2009-11-24
bump again?  Surely someone knows :-k

---

### Post by epsilon72 on 2009-12-02
Does the user switch applet even use the gnome-power-manager gconf settings?  Even the shutdown menu, the one you use if you remove the user switch applet, is different from its vanilla counterpart - it's been modified with what I like to call "special ubuntu sauce".  Like I said in the original post, hibernate still shows up there so I'm wondering if all of the "special ubuntu sauce" has broken some things with gconf.

---

### Post by epsilon72 on 2010-10-12
I know that this is an old thread, but I wanted to post the solution to this problem just in case someone comes across this thread via google or something (that's what I do when I have linux problems - ask google!)

Anyways, here it is:

Adapted from instructions here:
	[http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/](http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/)

To disable the "hibernate" and "suspend" buttons in gnome:

There will be a file called this or something similar:

	/usr/share/polkit-1/actions/org.freedesktop.upower.policy

It might not be named exactly that, but it will be something similar.

In this file, there will be sections for 'suspend' and sections for 'hibernate'.  In each of these sections, there will be a 

	<allow_active>yes</allow_active>

If you want to disable one or both, change the corresponding section's above line to

	<allow_active>no</allow_active>

This should disable those buttons in gnome's shutdown menu in distros that ship with pre-compiled kernels.

---

