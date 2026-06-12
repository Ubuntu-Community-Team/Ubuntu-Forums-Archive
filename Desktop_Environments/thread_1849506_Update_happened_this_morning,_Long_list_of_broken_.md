---
title: "Update happened this morning, Long list of broken things now."
date: 2011-09-24
forum: Desktop Environments
---

### Post by BanderSnoot on 2011-09-24
Hi,

I had tried to install and use GNOME earlier and ended-up with a strange hybrid.  I tried resetting and reinstalling packages, but nothing helped.  The good thing was that I could still choose "ubuntu classic (No effects)" and I'd get a nice desktop I could live with.

Update manager ran this morning for about an hour.  I could see a bunch of stuff being updated for the desktop, and I hoped things would get better.  Instead, things got worse.
[LIST=1]
[*]The login screen has changed.  I no longer have a choice bar at the bottom.  Instead I get a choice of ubuntu in the login box itself.  When I login, it's back to Unity, which I am starting to positively hate.
[*]The Preferences and Admin menus under GNOME are gone.  Now all I can do is a very very limited number (maybe 12) small settings under system settings.  I can't find any way to make adjustments to make stuff work in the desktop.
[*]The desktop itself no longer displays icons for files or stuff.
[*]The desktop no longer supports any action when you right click on it.
[*]The big thing is that GNOME seems to be completely gone and I can't get it back.  I am stuck with Unity.
[/LIST]

I am starting to think that ubuntu is too fragile and easy to break.  I really want to give it a try, but I hate the idea of doing a complete re-install from the beginning again just to get back to square one.

Can anyone help me get GNOME working again?  I had tried to reinstall before and it didn't work.  I am also reading that ubuntu will only support Unity in the future, with nothing else supported.

Can anyone suggest a working non-fragile alternative to Unity?

Is there a package I can install or remove or anything to get this working again?

Thank you.

---

### Post by BanderSnoot on 2011-09-24
One other thing.  There used to be a menu at the top where I could browse software apps and another called "Places" and I believe another that allowed for a lot of system settings and preferences.  I can't recall if this was only under GNOME or if it was there under Unity.  Now that is also gone, and I am hunting in vain through the list of apps under that pop-up dashboard thing.

---

### Post by BanderSnoot on 2011-09-24
And another thing.  Most of the windows now have no options to close, minimize or maximize.  I have to right click on the tile bar to close them.

Again, any suggestions would be appreciated.

---

### Post by sammiev on 2011-09-24
Gnome3 is not like gnome2 but if you log out and click on the button next to the password you will get a little drop menu where you can select gnome. :)

---

### Post by coffeecat on 2011-09-24
I was intensely puzzled by your first post until I read your previous thread. A few points. Unity is not fragile. Gnome is not fragile. But what you have done is to install gnome 3 into the gnome 2 environment of 11.04 using a ppa repository. Although Ubuntu makes it relatively easy to enable ppa repositories, ppa repositories are by their very nature 3rd party and some can break your system unless you are experienced enough. And many experienced users have ended up with broken systems when trying to mix gnome3 in 11.04's gnome2.

I'll give you a not very good analogy. It's a bit like trying to install Windows 7's aero in Windows XP. OK, I said it was a poor analogy, but hopefully you get the idea. :)

I'm sorry you've had this experience. Believe me, it is not typical. I'm usually loath to suggest a re-install, but in your case it might be quicker and easier, and at least then you will get the classic gnome 2 desktop that you seem to prefer.

By the way, although 11.10 will come with Unity only as default, it will be possible to install a package called gnome-session-fallback to give you a desktop very similar to classic gnome, so you don't have to use Unity if you do not want to. And as 11.10 is being built on gnome 3 you won't have to worry about conflicting gnome 2 and gnome 3 libraries and configurations.

---

### Post by BanderSnoot on 2011-09-24
Problem solved.

I did a clean wipe and reinstall.

---

