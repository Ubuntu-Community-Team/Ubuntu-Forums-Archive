---
title: "Closing firefox and amarok properly on shutdown"
date: 2007-12-04
forum: Desktop Environments
---

### Post by ltcmdata on 2007-12-04
Hi!
Every time I shut down KDE/Fluxbox and firefox is opened, the next time I start firefox I get the "Your last session closed unexpecedly" message.This means that firefox gets killed by KDE/Fluxbox.Is there any way, a script or something, that will close firefox properly on shutdown?
I have the same problem with amarok, but only with fluxbox.on fluxbox exit the playlist doesn't get saved.this problem doesn't exist on KDE, so I think there must be some way to solve it.

---

### Post by marpstar on 2007-12-04
As far as I know (and feel free to correct me, but) Firefox 2.0+ will always recognize a shutdown as an unexpected close because it, by default, wants you to have the opportunity to continue your last session.  You can, if you want, disable it so that it won't store your session no matter what by:

1. direct firefox to the address 'about:config'
2. in the filter, type 'sessionstore.enabled' and set it to false.  

That way it won't ever prompt you to resume your session.

As for Amarok, I don't know...

---

### Post by ltcmdata on 2007-12-05
I have installed firefox-3.0 and in KDE all works fine now.The problem is Fluxbox.It seems that on shutdown KDE closes programs differently.I will have to find out what the difference is.

---

