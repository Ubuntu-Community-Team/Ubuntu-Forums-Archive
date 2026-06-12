---
title: "Compiz Fusion shortcuts"
date: 2007-07-27
forum: Desktop Effects &amp; Customization
---

### Post by BDNiner on 2007-07-27
When i move my mouse to the top right hand corner all the windows get smaller and i can pick which window i want to focus on. Is there anyway i can change the corner? it is right next to the logout button, so if i want to shut down my computer it is a pain since the desktop's focus changes to the window selector.

---

### Post by tgm4883 on 2007-07-27
System > Preferences > CompizConfig Settings Manager

Scroll Down to window managment, then scale.

Click on the actions tab.  then expand general

There it is under "initiate window picker for all windows"

---

### Post by BDNiner on 2007-07-27
Thank you!

---

### Post by LegoAddict on 2007-09-03
What about Compiz on the Gusty beta?  I can't find any configuration options on Gusty.

---

### Post by psyopper on 2007-09-03
CCSM doesn't come preinstalled for Gutsy, but it's supposed to be in the repositories. If you are using Gutsy and have activated all of the repos try something along the lines of
```

sudo aptitude update
sudo aptitude install compizconfig-settings-manager

```

I'm pretty sure that's the package name in Gutsy. It's the default package name in the various other Feisty/Compiz repositories.

---

### Post by LegoAddict on 2007-09-06
Ok.  I'm running off the Tribe 4 Live CD because I get the feeling it's a tad too unstable to partition for and effects don't work under VirtualBox.

But it will be stable in October :D

---

