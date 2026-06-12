---
title: "&quot;Switch from ...&quot; / &quot;Switch User&quot; does not work"
date: 2011-02-15
forum: Desktop Environments
---

### Post by kenm_uk on 2011-02-15
Whenever I try to "Switch from [username]..." I get locked screen with the options to "Leave Message", "Switch User" or "Unlock".

If I click to "Switch User" the password box just disappears (as if one tried to unlock with an incorrect password).  The only thing I can do is unlock the screensaver and resume my login session.  I can not seem to switch users.

Does anyone know why "Switch User" is not working?  Any idea how I can find/fix this problem?

Thanks,
Ken


I am running Ubuntu 10.04 LTS (2.6.32-28-generic).

---

### Post by jerrrys on 2011-02-16
you have the system>admin>user settings set right

---

### Post by kenm_uk on 2011-02-16
> **jerrrys said:**
> you have the system>admin>user settings set right

Under "System > Administration" I don't see "User Settings".  There is a "User and Groups" option (but when I open that I don't see anything that looks relevant).

Do you have any suggestions?

Thanks,
Ken

---

### Post by jerrrys on 2011-02-16
i do not use this option, but wonder if the user has to be already active to switch or if turning off password in user/groups would be an option.

---

### Post by kenm_uk on 2011-02-16
> **jerrrys said:**
> i do not use this option, but wonder if the user has to be already active to switch or if turning off password in user/groups would be an option.

There is a circular inconsistency in your suggestion: If one can only switch to a logged in user, but a second user can never log in, then one can never switch users.  I don't think that is the answer :(

Also, I can't imagine Ubuntu created a switch user option which only works for users with no passwords... so that probably isn't the solution either :(

---

### Post by jerrrys on 2011-02-16
yes, of course only one user at a time, but a second user can be running and not logged in

---

### Post by kenm_uk on 2011-02-16
> **jerrrys said:**
> yes, of course only one user at a time, but a second user can be running and not logged in

I wonder if we are talking about the same thing...

My question has to do with one user being logged in to an Ubuntu/Gnome desktop.  A second user then wants to use the machine.  So she would usually click on the "Switch User" option from either a Gnome menu or from the screensaver password box.  This would allow the second user to login and use the machine and not logging out the first user.  The users can switch as needed between the two running login sessions.

However, when I click on "Switch User" it does not work.  It gives me the screensaver password dialog box and any attempt to "Switch User" just closes the box until the screensaver detects the next mouse/keyboard movement.

---

### Post by jerrrys on 2011-02-16
i did away with that button at install.  however there are two such buttons in 'add to panel' that i just tried.  maybe one will work for you

indicator applet session     or

user switch

---

### Post by kenm_uk on 2011-02-17
> **jerrrys said:**
> i did away with that button at install.  however there are two such buttons in 'add to panel' that i just tried.  maybe one will work for you

indicator applet session     or

user switch

Yes, I have "indicator applet session" on the panel. When I click on it I get options such as Lock Screen, Guest Session, Switch from [user]..., Log out..., Suspend, Hibernate, Restart..., Shut Down....

However, when I click on "Switch from [user]..." I simply get a screensaver locked desktop.  Any attempt to "Switch User" from the dialog box simply results in the dialog box disappearing until the next keyboard/mouse event.  The Switch User button does not work for me and I don't know why.

---

### Post by Krytarik on 2011-02-17
There seem to a couple of different failure scenarios currently when using the mentioned option.

At my mom's machine for example (she has an ATI card, running the Open Source Edge driver), when you choose those option you get a blank screen with blinking cursor. But I figured that there is the GDM login screen running at another session (Alt+Ctrl+F*), however I didn't actually tried to login at those. Back in Gutsy 7.10, while still able to run the proprietary driver, the system just froze at this point.

There seem to be particular issues when running the ATI/AMD proprietary driver.

Check if you also have the GDM login screen in another session, by trying all combinations of Alt+Ctrl+F* from F7 upwards. Also check your screensaver options, and if so try disabling the "lock screen" option.

---

