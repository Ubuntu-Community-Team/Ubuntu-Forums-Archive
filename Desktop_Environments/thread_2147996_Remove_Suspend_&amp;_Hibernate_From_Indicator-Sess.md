---
title: "Remove Suspend &amp; Hibernate From Indicator-Session"
date: 2013-05-23
forum: Desktop Environments
---

### Post by Kirk Schnable on 2013-05-23
I am working on a new customized Xubuntu 12.04 image to deploy to just under 1,000 computers this summer.  Due to power management problems with some of our hardware, I have disabled Suspend and Hibernate from functioning using the policy kit.  However, the options still appear on the drop-down menu for Indicator-Session. 

This tutorial worked for me, when I was disabling the suspend & hibernate functionality... [http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/](http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/)

I was successfully able to stop Suspend & Hibernate from working.  However, I can not get the options to disappear from Indicator-Session.  It is undesirable to have non-functional options present on the menu, which generate errors when clicked.  I'd rather just have the options gone.

I tried this tutorial: [http://ubuntuforums.org/showthread.php?t=1830829](http://ubuntuforums.org/showthread.php?t=1830829)
It succeeded in making the necessary xfconf booleans, however they did not have the desired effects.  You can see that they truly do exist, here...
[IMG]http://binaryimpulse.com/wp-content/uploads/2013/05/xfconf-screenshot.png[/IMG]

I would like to remove suspend & hibernate options from this drop-down...
[IMG]http://binaryimpulse.com/wp-content/uploads/2013/05/indicator-session-xfce.png[/IMG]

Any suggestions would be appreciated.

Thanks,
Kirk

---

### Post by Toz on 2013-05-23
Don't have a 12.04 install handy, but in 13.04 you can right-click the Action Buttons applet and select Properties. There you can enable/disable menu items (Actions).

---

### Post by Kirk Schnable on 2013-05-23
> **Toz said:**
> Don't have a 12.04 install handy, but in 13.04 you can right-click the Action Buttons applet and select Properties. There you can enable/disable menu items (Actions).

Unfortunately, on Xubuntu 12.04, this is not an option.

[img]http://binaryimpulse.com/wp-content/uploads/2013/05/indicator-session-xfce-right-click.png[/img]

---

### Post by Toz on 2013-05-23
Have a look at [this thread]("http://askubuntu.com/questions/278155/how-to-change-the-hibernate-and-suspend-settings-at-a-system-wide-level-in-xfce") about kiosk mode - looks like it might work in 12.04.

---

