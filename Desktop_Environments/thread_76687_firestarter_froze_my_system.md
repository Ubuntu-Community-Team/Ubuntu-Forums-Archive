---
title: "firestarter froze my system"
date: 2005-10-15
forum: Desktop Environments
---

### Post by yesplease on 2005-10-15
Ubuntu is completely frozen, the desktop looks normal but I cant do anything. 

Edit: **SOLVED! It is not my intention to suggest that Firestarter is a bad program, I should have used a different title for this post. **

firestarter has an annoying message when gnome starts: You must have root privilages to run FireStarter.

In order to remove this message I did:

First of all, since Firestarter requires sudo privileges to be started, we will add it to /etc/sudoers:

Code:

export EDITOR=gedit && sudo visudo


and add the following string at the bottom:

Code:

username ALL=NOPASSWD:/usr/sbin/firestarter


where "username" is YOUR OWN user name.

Now let's add it to the session.
Open "System->Preferences->Sessions" and click the tab "Start up programs" (the last).
Click the "Add button" and add the following string:

Code:

gksudo /usr/sbin/firestarter

all according to this tread: [http://ubuntuforums.org/showthread.php?t=26483&highlight=firestarter](http://ubuntuforums.org/showthread.php?t=26483&highlight=firestarter)

Firestarter still produces it message, but now on top of a window (i think it is a window where you have type your password).

I can still move the mouse, but I cant do anything with it. I cant open an application or remove firestarter. The keyboard seems to work (I can do ctrl-alt-F, but I dont know what to do on these screens).

---

### Post by yesplease on 2005-10-15
I solved it by dumb luck, and by typing my password. 

It appeared that the window beneath firestarters extremely annoying pop-up was a password window, and that it got the password that I typed blindly. This started up firestarter. 

I completely removed firestarter and related stuff (mentioned in the  post above).

---

