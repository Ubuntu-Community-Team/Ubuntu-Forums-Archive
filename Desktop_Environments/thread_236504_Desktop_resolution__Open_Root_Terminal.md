---
title: "Desktop resolution?  Open Root Terminal?"
date: 2006-08-14
forum: Desktop Environments
---

### Post by kargath64 on 2006-08-14
Well, I've got two (hopefully) quick questions for Ubuntu Dapper.

First - how can I set my desktop resolution to 1280x1024?  I can set the resolution in the dialogbox to 640x480, 800x600 and 1024x768, but my monitor res is a native 1280x1024, and I prefer non vaselinevision for my computer.  I think I have to edit the Xorg config file, but I prefer not to mess about with that unlessI know what I'm doing (or have instructions from someone else who does :) )

The other issue regards terminals.  How do I right-click a folder or empty folder space/desktop and have a menu item to "Open Terminal Here" like in Red Hat?  I do a fair bit of terminal opening/closing, and it would save me a few seconds each time.
Also, whatever happened to the "Open Root Terminal" option from the original Ubuntu (5.04)?  And how can I get it back?

---

### Post by ardchoille on 2006-08-14
> **kargath64 said:**
> Well, I've got two (hopefully) quick questions for Ubuntu Dapper.

First - how can I set my desktop resolution to 1280x1024?  I can set the resolution in the dialogbox to 640x480, 800x600 and 1024x768, but my monitor res is a native 1280x1024, and I prefer non vaselinevision for my computer.  I think I have to edit the Xorg config file, but I prefer not to mess about with that unlessI know what I'm doing (or have instructions from someone else who does :) )

The other issue regards terminals.  How do I right-click a folder or empty folder space/desktop and have a menu item to "Open Terminal Here" like in Red Hat?  I do a fair bit of terminal opening/closing, and it would save me a few seconds each time.
Also, whatever happened to the "Open Root Terminal" option from the original Ubuntu (5.04)?  And how can I get it back?

**1.** Please make a backup of your xorg.conf file before editing it:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
That copies the xorg.conf file to xorg.conf.bak as a backup in case you need it later.

Then, the proper way to edit the xorg.conf file in Ubuntu is:

```

sudo dpkg-reconfigure xserver-xorg

```
Notice the lack of spaces before and after the "-"'s. That will ask you some questions and then save the new setting to xorg.conf. When you are done with that, log out and restart X with CTRL+ALT+BACKSPACE


**2.** To get the open terminal menu item on right-clicking a folder or the desktop, do:

```

sudo apt-get install nautilus-open-terminal

```
I'm not sure if that takes effect immediately, or whether you need to log out and back in to see it. But, since you're going to log out after step one anyway, may as well do step two before logging out :)

---

