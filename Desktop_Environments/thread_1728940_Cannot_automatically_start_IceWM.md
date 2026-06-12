---
title: "Cannot automatically start IceWM"
date: 2011-04-14
forum: Desktop Environments
---

### Post by Fraoch on 2011-04-14
I've been experimenting with various lightweight do-it-yourself Ubuntu installs in a VM following these instructions:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

The Openbox installation went well except for some minor cosmetic concerns which I'll cover in another thread.  It's the IceWM install which I have a question about.

To login and autostart X, I'm using this handy little trick:

[http://ubuntuforums.org/showpost.php?p=3429544&postcount=3](http://ubuntuforums.org/showpost.php?p=3429544&postcount=3)

Very slick and saves me from using a login manager.

It works perfectly on the Openbox install, but on the IceWM install it won't work.  There wasn't even a .bash_profile file - I created one but the system seems to ignore it.  Heck, there isn't even an .xinitrc file, so I actually have no idea how IceWM is called after X is started (it is, somehow, as I don't have to start IceWM once X is started).

So now I login to the command line, then I start X.  I'm pretty sure it doesn't have to be this way but with the system ignoring .bash_profile and .xinitrc I'm not sure how to proceed.

(Incidentally Openbox has the edge over IceWM - it consumes about 5 MB less of memory even with an fbpanel taskbar, it's snappier, prettier and easier to configure.  IceWM is more configurable but that 1300-line preferences file takes some time to go through!)

---

