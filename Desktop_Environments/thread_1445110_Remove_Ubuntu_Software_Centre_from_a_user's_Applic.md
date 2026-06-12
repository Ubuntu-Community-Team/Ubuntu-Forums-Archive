---
title: "Remove Ubuntu Software Centre from a user's Applications menu?"
date: 2010-04-02
forum: Desktop Environments
---

### Post by Gömböc on 2010-04-02
For the purposes of creative writing, I want to be able to implement a very barebones Ubuntu (GNOME) environment, with no distractions. I want access to a limited set of applications (perhaps only gedit and OpenOffice.Org Writer) and no internet access. All there must be is a word-processor with a blinking cursor. Of course, I'll retain my full-privileges user ID: but to switch to that will be a conscious decision, rather than a casual drifting into time-wasting.

I have gone about this by creating a new user called "writer". As admin, I've removed almost all user privileges for writer. Then, I've signed on as writer and have used System > Preferences > Main Menu to remove all but two or three applications from the menu.

When I have everything as I want it, I'll remove the ability to edit the menu using the guidance here:

[http://ubuntuforums.org/showthread.php?t=928847](http://ubuntuforums.org/showthread.php?t=928847)

My problem is that, at the bottom of the Applications menu, there is an entry for Ubuntu Software Centre, and this cannot be removed using the Main Menu applet. Browsing through the list of applications looks like a great way to waste a few hours. (Granted, I won't have access to the internet, so I won't be able to download anything, but I don't want to see it there, tempting me to switch to my admin account and download stuff.) Is there any way to remove Ubuntu Software Centre from the Applications menu for a specific user, please?

---

### Post by ajgreeny on 2010-04-02
On my system, using the main menu, not the menu bar, there is an item for the software centre shown at the bottom, on the right pane of the menu editor window.  I assume it could be deleted in that window the same as any other, or you could just set it not to show, if you prefer.

Provided the user "writer" can not edit the menu, he or she could not add it back in and then waste time looking at application info that he can not install.  Of course, that would not stop any user simply using terminal or Alt+F2 to run anything they want, even if they can't actually use it.

---

### Post by Gömböc on 2010-04-02
> **ajgreeny said:**
> On my system, using the main menu, not the menu bar, there is an item for the software centre shown at the bottom, on the right pane of the menu editor window.  I assume it could be deleted in that window the same as any other, or you could just set it not to show, if you prefer.

You're absolutely right. I don't know why I didn't see it before. I'm an idiot. Thank you!

---

