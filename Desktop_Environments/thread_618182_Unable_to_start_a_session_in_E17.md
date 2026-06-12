---
title: "Unable to start a session in E17"
date: 2007-11-20
forum: Desktop Environments
---

### Post by anthonie on 2007-11-20
Hi all,

I have had E17 on my machine for a year or so. Everything worked fine until I upgraded my Feisty distro. After that E17 would crash on occasion, however, nothing serious though.

I login by default in a GNOME session, E17 is just for play and learn.
Normally I start a different session, exiting GNOME and returning to the login screen.
When I try to login to E17 with my default user account, it won't work, even though E17 is installed correctly. Logging in as anthonie will just bring me back to GNOME. However, after  I allowed root to be logged in from the login-screen, it will get me to E17, but only as a root. 
Strange thing is: It does not confirm anything like it used to. It used to ask if I wanted to log in to this session as default or just for this session. Now it doesn't ask that at all. As root it just logs me in

In another threat I read somebody solved a common problem by chowning the .ICEautority back to his normal useraccount. For me that did not work, because it is already set like that.

So, I'd like to know whether my E17 is completely broke and I should start building it from scratch again or is there something that can be done? 

Regards,

Anthonie

---

### Post by smartboyathome on 2007-11-20
Did you copy the .desktop file to your GDM folder, or did you symlink it? If you copied it, did you upgrade recently? There have been problems with E17 because the file was copied instead of symlinked.

---

### Post by anthonie on 2007-11-21
I honestly don't recall it. After upgrading my Feisty to more recent versions things were so screwed up that I decided to do a fresh install, which is the stage where I'm at right now.

As soon as this Feisty is upgraded and working I'll be reinstalling E17 again.

---

