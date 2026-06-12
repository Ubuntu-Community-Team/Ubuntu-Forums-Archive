---
title: "Beryl+Ati+Dapper= Nothing?"
date: 2007-02-10
forum: Desktop Environments
---

### Post by Shampyon on 2007-02-10
I added the necessary repos and made sure I'd installed Beryl, themes and XGL. For some reason, though, Beryl just won't start up. I try switching the window manager to beryl through beryl-manager, and it stays with metacity. I try choosing an XGL session at login, with beryl-manager as a startup app, and it still loads metacity.

What could I be doing wrong?

I know a lot of people recommend going up to Edgy to make it easier, but unfortunately when I tried Edgy my system just wouldn't work properly. I could only get my graphics and sound running right under Dapper, so I'm sticking with it until either it's no longer LTS or until Edgy reaches the LTS stage.

EDIT: It looks like Beryl is crashing and the system switched back to Metacity.
Also, for some reason Metacity isn't working properly now either. The container windows, with the close/minimise, maximise buttons? They're gone. No app, not even nautilus, has them now.
Everything's gone pear-shaped :(

Edit 2: Figured that last error out: I hadn't re-enabled the fallback option in beryl-manager. It was trying to use beryl and half-failing. Once re-enabled, the fallback switched things back to metacity and my system is useable again. Still can't get beryl to work, though...

---

### Post by fjm03 on 2007-02-10
Here's my experience with Dapper and Beryl and hopefully it wiil help you.

The Beryl project is apparently concentrating on the current Ubuntu distribution (Edgy) and, as a result, Beryl 0.1.1 is the last version of Beryl available for Dapper. The current version of Beryl (0.1.9xx) is  available for Edgy and the 0.2 version, scheduled to be available later this month, will probably  only be supported in Edgy.

There are many  HOWTOs available regarding installation of Beryl on Ubuntu. Several are located on this forum. Make sure you understand the date of the HOWTO that you use. The most current HOWTOs are not necessarily located on the Ubuntu forum. Try the Beryl Project for up-to-date information.

Because Dapper is restricted to an older version of Beryl, which was less stable and also gave me problems, I  chose to first upgrade to Edgy, per this forum's guidelines, and then installed Beryl. With Edgy there is an automatic script available on the Beryl Project site to install Beryl. It's painless for beginners.

I find  Edgy, either  under Metacity or under Beryl 0.i.9xx, to be very stable.

---

