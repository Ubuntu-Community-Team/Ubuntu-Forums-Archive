---
title: "Compiz No Show Mouse or Burn Effects"
date: 2009-05-11
forum: Desktop Environments
---

### Post by prickee on 2009-05-11
I'm running Jaunty and I'd like to enable Show Mouse under Compiz-Accessibility but it doesn't exist like it did in Intrepid.  I also noticed no Burn option under Animations.  All of my desktop effects are working and extras & unsupported are enabled under compiz.

I've searched for like 4 hrs.  Thanks in advance...

---

### Post by PacSci on 2009-05-11
It's there on my computer. My suggestion is to make sure that the Animations Add-On is enabled, as well as Mouse position polling, as Burn is in the Animations Add-On, and Show Mouse needs Mouse position polling to work.

---

### Post by prickee on 2009-05-11
Hmmm wow I wonder....I have no Animations Addon in my Compiz.  Should I re-install???? Here's the screens as proof.

---

### Post by prickee on 2009-05-14
OK
Call this one fixed.  It took some time & research but I found out what the problem was.  Here is the link and highlighted fix action.  

[http://ubuntuforums.org/archive/index.php/t-1128345.html](http://ubuntuforums.org/archive/index.php/t-1128345.html)

[COLOR="Red"]Ok guys, I think I've figured out the problem. I have been using the 3rd party Compiz repository, when I upgraded to Jaunty there was an update to a compiz package which then made the "Animations Add-on" tab disappear.

So what I did is disable the 3rd party compiz repository, reloaded my sources, went into synaptic and searched for "compiz-fusion" I then marked both "compiz-fusion-plugins-main and "-extra" for "complete removal" then logged out and logged back in and then installed those 2 again and it worked. So basicly disable the 3rd party compiz repository, uninstall those 2 packages and reinstall them making sure the 3rd party repository is disabled.

I hope this helps you guys.[/COLOR]

---

