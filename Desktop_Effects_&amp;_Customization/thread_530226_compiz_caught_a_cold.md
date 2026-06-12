---
title: "compiz caught a cold"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by sdowney717 on 2007-08-20
why do they send out updates that are so obviously broken?

---

### Post by KhaaL on 2007-08-20
Appearently they aren't broken to some users... I spoke to trevino and he didn't experience any of the problems most of the users here are having...

I haven't heard anything from people using vorians or amaranths repositories with these problems though, which are you using?

---

### Post by sdowney717 on 2007-08-20
installed thru synaptic
I am showing a snapshot of my sources

---

### Post by KhaaL on 2007-08-20
You're using treviños repos i see. It's not his fault, it seems to be something faulty with the release, as quoted from their blog:

> 
IMPORTANT:

If you are currently using CCSM, LibCompizConfig, CCP and the like to configure compiz, it is absolutely essential that you do not update the compiz-core package for a while, because you will lose the ability to set any options. The reason for this is because of a re-write of action handling in core, as well as a re-write of the gconf plugin.
(source is [here]("http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/"))



You have two choices, either wait for the next update, or go with Vorian's repos - [http://vorian.org/?p=82](http://vorian.org/?p=82) 

Good luck!

---

### Post by FuturePilot on 2007-08-20
Everything is working fine now. You just need to completely remove the Unsupported Plugins package and then reinstall it. Then restart compiz-fusion and all should be working again.

---

### Post by KhaaL on 2007-08-20
> **FuturePilot said:**
> Everything is working fine now. You just need to completely remove the Unsupported Plugins package and then reinstall it. Then restart compiz-fusion and all should be working again.

Your advice did not work for me. I tried with:

$ sudo apt-get --purge remove compiz-fusion-plugins-unsupported

followed by $ sudo apt-get clean and autoclean. Restarted X and then reinstalled it. I still have the same symptoms.

---

