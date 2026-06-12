---
title: "Shut down and Restart buttons missing from Logout Menu"
date: 2008-11-08
forum: Desktop Environments
---

### Post by theWrkncacnter on 2008-11-08
After upgrading to Intrepid, a dialogue asked me to upgrade my logout menu so it would also handle instant messages and quick user switching. However in doing so, it made my Shutdown and Restart buttons disappear (Now they're under "System." How can I get them back in the logout menu?

Additional info: The buttons are where they belong in some other accounts on this computer.

Also: A launchpad answer suggested checking that System>Administration>Login Window>Local preference for "active menu" was checked, and yes it is checked.

Thank you for your help!

---

### Post by OzzyFrank on 2008-11-21
OK, what seems to be happening is that there is now actually a Log Out button and a Shut Down one... and (don't ask me why) it seems the default button is now the former rather than the latter, as it should be. This is EASILY fixed, not like when this happened in other versions (had to manually fix it or wait for an update).

Right-click your panel, choose +Add To Panel, scroll down till you find "Shut Down..." and drag that to your panel. You can then delete the logout one, though note that the shutdown one no longer has options for switching user (ie: just logging out to the login screen)... for those who find that a problem: keep both buttons; for the rest of you: if you ever need to log out only, do it from the System menu (no big deal really for most of us).

Hope this helps! Cheers.

---

### Post by zman58 on 2008-12-23
> **theWrkncacnter said:**
> After upgrading to Intrepid, a dialogue asked me to upgrade my logout menu so it would also handle instant messages and quick user switching. However in doing so, it made my Shutdown and Restart buttons disappear (Now they're under "System." How can I get them back in the logout menu?

Additional info: The buttons are where they belong in some other accounts on this computer.

Also: A launchpad answer suggested checking that System>Administration>Login Window>Local preference for "active menu" was checked, and yes it is checked.

Thank you for your help!

On Ubuntu 8.04.1 desktop I noticed this problem. I was missing Restart and Shutdown when I selected the logout menu (little green guy running). The only choice offered in the lower part of the dialog box was "Hybernate". To remedy this I went into:
    "System - Administration - Login Window"
I selected the tab "Local" and selected the item titled:
    "Show Actions Menu".
That did the trick. I now have "Hibernate", "Shutdown" and "Restart" selections available when I select the Logout item from the panel. :D
I did not realize that earlier, while playing around with login settings, I had inadvertently unchecked this item.

---

### Post by theWrkncacnter on 2009-01-21
Thanks for your help guys, I haven't posted in a while because it's not that big of a deal, but I would still like to get this fixed. Something fishy is going on.

Most of the time, shutdown restart and hibernate are missing from my logout menu. But sometimes, for no explicable reason, and following no pattern I can see, the missing options ARE there. But most of the time they are missing.

I've checked and double checked but Login Window>Local>Show Actions Menu IS selected. The problem persists.

Any ideas? Solutions? Things I should try?
Thanks.

Edit: PROOF!
[[IMG]http://img50.imageshack.us/img50/3391/logoutmenuvs1.png[/IMG]](http://img50.imageshack.us/my.php?image=logoutmenuvs1.png)

---

### Post by lunatico on 2009-01-23
Since we are playing with the two options of shutdown buttons here. How do I get the original Intrepid button back? When I switched to Intrepid and noticed that the shutdown button also had my Pidgin status I didn't liked it so much, but now I think I want to try it but I don't see it on the Add to Panel options. Any ideas?

---

### Post by lunatico on 2009-01-23
> **lunatico said:**
> How do I get the original Intrepid button back?

Never mind.... it is on the Add to Panel options. It's call User Switcher...

---

### Post by theWrkncacnter on 2009-01-28
I still need to know how to get the missing options back -- my brother has them on his user account on this computer.

---

### Post by foodude on 2009-02-04
Same problem here now..

---

### Post by scuicho on 2009-02-05
Right click on a panel and open the add menu- scroll down to (Main Menu) add it to a panel,doesn't  matter where, click on it go down to (log out,Your name) then drag it to the panel where you want it.

---

### Post by prkos on 2009-02-09
I remember on one laptop I recently installed ubuntu and there were all options in one window: logout, switch, shutdown, hybernate, restart. 

On my desktop it's separate, maybe there's another applet that holds them all?

---

### Post by michalh on 2009-02-17
maybe this can help

gconf-editor /apps/fast-user-switch-applet/show_presence_info

---

### Post by prkos on 2009-02-17
I have it ticked, should I untick it?

---

### Post by fhl on 2009-02-24
The suspend/hibernate/restart/shutdown options on the user switcher button menu are enabled by the power manager service.

Go to System/Preferences/Sessions and scroll down to the Power Manager service and tick it. Then log out and log back in again. You should now see the extra options in the user switcher button menu.

Hope this helps someone!

---

### Post by prkos on 2009-02-25
It wasn't exactly the same on my machine but it is a workaround. 

I didn't have Power manager option under Sessions, but I went to System > Administration > Services and turned on Power management there. 

I added the User switcher to the panel and after a restart I can see all the options in a popup menu when clicking on the icon. I'm now using User switcher instead of the Shut down applet, it's a bit weird because the way icon looks like doesn't quite suggest its purpose, at least not in the way I use it, where most used options are Logout, Restart and Shutdown, not switching users. 

But it still isn't the thing I had in mind, where all options appear together in Shutdown or Logout window. I can see the logic behind separating the two, but maybe some third applet could make more sense for keeping the options together, I can't think of a name for it though.

---

### Post by Ampersand. on 2009-03-24
Zman58: You saved me several days of waiting for a reply to a new thread with your advice on the login window thing.. I was about to create a new one then decided to 'just look at one more' and i found your reply.
Thanks

---

### Post by theWrkncacnter on 2009-03-24
Unfortunately mine is still not fixed.
Sometimes I see the complete shutdown menu (Log Out, Shutdown, Restart, Hibernate), but other times I just have Log Out, the way it looks in the picture.

I wish I knew why it was different.

---

### Post by lud on 2010-02-06
Well, I had similar problem to yours, maybe it will help you somehow.

My menu for logout, shutdown, restart and all that stuff completely dissapeared.

I made a right click on the panel, chose 'add to panel' option and then added 'User Switcher' and everything was as it was before it dissapeared.

---

### Post by hariks0 on 2010-02-06
Try adding 'indicator-applet-session':popcorn: to your panel.

---

### Post by OzRattler on 2010-05-18
Tried all the above and the "Restart" and "Shutdown" choices are missing.  Even if I include a widget etc, I am only presented with "Logout" or "Lock" options.

To shutdown PC, I have to logout and *then* Shutdown.  Inconvenient.

Thanks!

---

### Post by hariks0 on 2010-05-20
> **OzRattler said:**
> Tried all the above and the "Restart" and "Shutdown" choices are missing.  Even if I include a widget etc, I am only presented with "Logout" or "Lock" options.

To shutdown PC, I have to logout and *then* Shutdown.  Inconvenient.

Thanks!

Try some key bindings for shutdown. Follow the link in my signature. I have set 'Super+l' as logout etc.

---

### Post by CJ_Hudson on 2010-05-23
I had a similar problem except my shut down button was also missing from the System menu!
Please, I now have two shutdown buttons. How do I get rid of one?

Ah, right-click on it and 'remove from panel' Easy!

---

