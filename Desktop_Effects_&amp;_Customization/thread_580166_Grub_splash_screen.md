---
title: "Grub splash screen?"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by kdarkentity on 2007-10-18
How do you install a different background or splash screen for the grub?

---

### Post by Vadi on 2007-10-18
help.ubuntu.com/community says... [click me]("https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29#head-616e8477b76f70cdd317812fef0ac88b248e25b4")!

But that's just so you get the hang of what you're going to do. There's a really easy graphical way, via the Start-Up Manager.

Get it by installing it, so either add/remove and search for it, or open the terminal (applications-accessories-terminal), and copy/paste this:

sudo apt-get install startupmanager

Once you get it, head over to system - administartion - startupmanager. Click the appearance tab, and there you can manage your grub splash screen, and your ubuntu splash screen.

The difference between these two is that the grub one is shown behind the grub menu, once that dissapears, and you get a black screen with an orange bar, that's ubuntu's splash screen.

Feel free to ask if you need any more help!

---

### Post by victorgreen on 2008-07-10
Awesome, I hadnt known about startup manager. As an aside, sudo apt-get install bum    the bootup manager. Easiest way to edit startup services and get rid of random stuff you may not need- bluetooth, assistance stuff... etc

---

### Post by sankz on 2008-07-20
The easiest method is available here:
[http://fasterthanlight.wordpress.com/2008/07/18/beef-up-your-grub-loader/](http://fasterthanlight.wordpress.com/2008/07/18/beef-up-your-grub-loader/)
and here:
[http://fasterthanlight.wordpress.com/2008/07/20/create-your-own-grub-splash-image/](http://fasterthanlight.wordpress.com/2008/07/20/create-your-own-grub-splash-image/)

---

