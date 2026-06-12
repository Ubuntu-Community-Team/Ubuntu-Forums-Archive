---
title: "Black Screen with Mouse Pointer on Login After Upgrade to Ubuntu 9.04"
date: 2009-07-18
forum: Desktop Environments
---

### Post by lordofthebrambles on 2009-07-18
I am having a problem similar to what some other people have posted about, but I have not been able to resolve it.  After a distribution upgrade from Ubuntu 8.10 to 9.04, I began getting a black screen with a white mouse pointer, after logging in.  No matter how long I wait, that is all I see.

A failsafe Gnome session does work.  Also, other user accounts on my system are not experiencing the same problem - it is only happening for me.  (The other user accounts were created under Ubuntu 8.04 and are not as heavily customized as mine.  My account has been around for much longer, through several distribution upgrades, and I have customized a lot of the desktop settings.)

I tried deleting my desktop settings through the following commands, but this had no effect:

mv .gnome2 .gnome2.bak
mv .gnome2_private .gnome2_private.bak
mv .gconf .gconf.bak
mv .gconfd .gconfd.bak
mv .compiz .compiz.bak
mv .config .config.bak

Still, I would get the black screen after logging in, so I restored all of my settings and tried some other things.

I tried remove compiz, with the following command, and this had no effect:

apt-get remove compiz compiz-core.

I tried the following command:

apt-get install ubuntu-desktop

However, all packages were current and this did not result in any changes to my system.

I tried logging in using a failsafe session, turning off visual effects, and then logging back in with a normal Gnome session, but this didn't work either - I still saw the black screen.

At this point I can't think of anything else to try.  My system is still usable, but I have to login using a failsafe session, and I do not have access to my desktop settings.  Any suggestions?

---

