---
title: "Trying to back out Lucid weirdness"
date: 2010-06-09
forum: Desktop Environments
---

### Post by unkilbeeg on 2010-06-09
I'm trying to set up a master machine to be a template in all my labs, but Lucid has made some massive changes to the user interface, so I need to figure out how to back some of these out.  I'm hoping someone here can give me some advice.

1)  Fast User Switcher -- This is a really bad idea for a non-SOHO environment.  I'd like to not only remove the applet, but completely remove the ability for students to access this capability.  This thread gives some pretty clear instructions, but alas, it doesn't seem to work any more: [http://ubuntuforums.org/showthread.php?t=700675](http://ubuntuforums.org/showthread.php?t=700675)  Is there another way to do this?  It would be nice to allow them to log out, but NOT have the "Switch User" option show up in the dialog box.  What would be ideal, of course is the old "Logout" applet that listed "Shutdown", "Logout", "Restart", etc, but did not include Switch User.

2) Lock Screen -- On a private machine this is a necessity.  On public machines this is a really bad idea.  I need to disable this capability, and make sure that neither the student nor the screensaver can ever lock the screen.

3)  I *think* I've successfully eliminated the social networking user status junk.  We'll see.  :)

4) I *think* I've eliminated the face chooser on GDM, although it looks like I'm stuck with a "click to login" pre-login dialog.  That's irritating, but it's not as bad as having the face browser come up.

As I work through this template machine, I'll probably have other issues that I hope someone else has already solved, but this right now this is what I'm looking for.

---

### Post by BoneKracker on 2010-06-09
I'm no Gnome expert by any means, but I'm aware of two applications that might be useful to you:

sabayon (the application, not the linux distro)
pessulus

Another thing you might want to look into (long term) is LTSP.

---

### Post by spezticle on 2010-06-15
> **BoneKracker said:**
> I'm no Gnome expert by any means, but I'm aware of two applications that might be useful to you:

sabayon (the application, not the linux distro)
pessulus

Another thing you might want to look into (long term) is LTSP.

neither sabayon nor pessulus effecively disabled or removed switch user. it prevented the menu item 'lock screen' but not switch user. at least not with 9.10 Karmic anyway

---

### Post by mjuhasz on 2010-06-16
Both lock screen and fast user switching can be disabled with the gconf-editor. The keys are as follows:

/desktop/gnome/lockdown/disable_lock_screen
/desktop/gnome/lockdown/disable_user_switching

---

### Post by mjuhasz on 2010-06-16
> **unkilbeeg said:**
> What would be ideal, of course is the old "Logout" applet that listed "Shutdown", "Logout", "Restart", etc, but did not include Switch User.

In case you want to remove the suspend and hibernate options as well you can create a file with the content below. It requires restart to take effect.

gksu gedit /etc/polkit-1/localauthority/50-local.d/disable-suspend.pkla

[Disable suspend]
Identity=unix-user:*
Action=org.freedesktop.upower.suspend;org.freedesktop.upower.hibernate
ResultActive=no
ResultAny=no

---

### Post by Crispy2 on 2010-07-10
@mjuhasz is right but he has a typo in his file should be (no space after freedesk):

```
[Disable suspend]
Identity=unix-user:*
Action=org.freedesktop.upower.suspend;org.freedesktop.upower.hibernate
ResultActive=no
ResultAny=no
```

edit: its not a typo but if you put the above in without using code it removes one of the periods and turns it into a space...

---

