---
title: "no shutdown option?"
date: 2006-05-31
forum: Desktop Environments
---

### Post by ThrobbingBrain66 on 2006-05-31
After I upgraded to Dapper LTS, there is no shutdown option on the applications menu.  I have Switch User, Lockout Session and Logout, but no Shutdown.  Anyone know if this is just missing in the LTS or where it is and how I can add it?

---

### Post by Jucato on 2006-05-31
Logout will launch the dialog box where you get to choose to end your current session, restart the pc, or shutdown.

---

### Post by ThrobbingBrain66 on 2006-05-31
Unfortunately it doesn't.  When I choose to logout, a box with a sleeping dragon pops up and my only option is to "End Current Session"  which takes me to the login screen.

---

### Post by Jucato on 2006-05-31
That's probably because you logged into X from the command line (that is, when you booted/rebooted, you didn't get directly logged into X, just the command line log in). 

Try restarting your computer and see what happens.

---

### Post by ThrobbingBrain66 on 2006-05-31
Maybe I can be more clear.  It's been about 3 days or so since I upgraded to Dapper LTS, two days since I've been using KDE over Gnome.  In that time I've booted and reboot multiple times and it's always the same.  There is no option to shutdown ever.

---

### Post by ThrobbingBrain66 on 2006-05-31
Update:  I've found the options that should allow me to shutdown from the logout menu, but nothing changes when I change them to what I think they should be.

In Kubuntu Dapper, they can be found in System Settings > KDE Components > Session Manager

---

### Post by Jucato on 2006-05-31
What happens when  you have:
- Confirm logout enabled
- Offer shutdown options enabled
- Default shutdown option: Turn off computer chosen

Btw, you installed KDE over Ubuntu by installing the kubuntu-desktop right? Are you using GDM or KDM as your default DM? I'm not sure if it's really related though.

---

### Post by ThrobbingBrain66 on 2006-05-31
I previously tried having those exact options checked and nothing happened.  Just to be sure I checked them all again, and still no option to shut down.  

Yes, I did install KDE over Ubuntu with kubuntu-desktop.

If it helps any, I booted into Gnome just now too, and there is no shutdown option there either.  When I clicked on Quit, it gave me every option but Shut Down.

---

### Post by ThrobbingBrain66 on 2006-06-01
SUCCESS!!!

Under Settings > Login Window > Local tab, I had Show Actions Menu unchecked, now all is well.  Thanks for your help Fenyx!

---

