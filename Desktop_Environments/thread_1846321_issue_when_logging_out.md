---
title: "issue when logging out"
date: 2011-09-18
forum: Desktop Environments
---

### Post by Todd_1215 on 2011-09-18
Hi ubuntu'ers - I recently switched to natty "clean install" and when I logout it seems like it switches to a virtual terminal "F7" where you see the remainder of services that started, etc ... Then after a few seconds it switches back to the login screen. Is it because of the way that it's been coded to work? If so it's very kludgy and I would think it should be addressed.

I know gdm manages the login session as well as the window session so is it using multiple X sessions to do the login and then another for the desktop?

My video card is:
> 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)


ubuntu has been making some good headway in the bootup and login experience but I think there is some room for improvement.

---

### Post by Krytarik on 2011-09-18
Yep, GDM's login screen itself is an X session. That's why you see those delay and the typical X startup behaviour.

You could try LightDM if you like, it will be the default display manager from Oneiric 11.10 on, which will be released in less than one month (October 13th) and is currently in beta state. Infos on both available options:

[http://www.tuxgarage.com/2011/06/testing-new-login-manger-for-ubuntu.html](http://www.tuxgarage.com/2011/06/testing-new-login-manger-for-ubuntu.html)

[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview)

Greetings.

---

### Post by Todd_1215 on 2011-09-19
Tried using lightDM on natty, but it's kind of ugly and there's no mouse available. I guess I'll stick with GDM for now. I'm not a big fan of Unity so I may just stay on Ubuntu Classic for now.

---

