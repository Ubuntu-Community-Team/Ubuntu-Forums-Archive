---
title: "Uninstall Compiz on 11.04"
date: 2011-06-01
forum: Desktop Environments
---

### Post by Bucic on 2011-06-01
Can I completely uninstall Compiz on 11.04? I ran out of options and I'd like to try it out as a part of desperate troubleshooting

If it can't be done, can I alternatively use this [http://lh5.googleusercontent.com/_1QSDkzYY2vc/TbiXT6XxnXI/AAAAAAAAEJs/AG1lwmZy8BE/ccsm2.png](http://lh5.googleusercontent.com/_1QSDkzYY2vc/TbiXT6XxnXI/AAAAAAAAEJs/AG1lwmZy8BE/ccsm2.png) to disable compiz completely by unchecking the "Enable Ubuntu Unity Plugin"?

If none of the above, how do I disable all potentially problematic desktop effects some other way?

EDIT:
Related topic: [http://ubuntuforums.org/showthread.php?t=1763670](http://ubuntuforums.org/showthread.php?t=1763670)
The advise is to log in to *"Ubuntu Classic (Without effects)"* session but I would still like to get an answer to my original question as I might want to still try Unity, without compiz (if it's possible at all).

---

### Post by Copper Bezel on 2011-06-01
Unity is a Compiz plugin. You can, however, look into installing unity-2d, which is available in the repositories and can be run under Metacity, the other, non-effects window manager.

---

### Post by Valsodar on 2011-06-01
I also experienced issues with the new compiz (0.9 is a complete rewrite of compiz) and it just kept crashing after few minutes of use. Don't know what the problem is but it did not work for me (shame as I like the new plugins). 

I fixed it by downgrading to the old compiz and sticking with that version. I still have the debs which I took from the debian site. Here is a list of the ones you need:

compizconfig-backend-gconf 0.8.6-0ubuntu2
libcompizconfig0 0.8.6-0ubuntu2
compiz-core 0.8.6-0ubuntu2
compiz-fusion-plugins-main 0.8.6-0ubuntu2
compiz-gnome 0.8.6-0ubuntu2
compiz-plugins 0.8.6-0ubuntu2
libdecoration0 0.8.6-0ubuntu2
compiz-fusion-plugins-extra 0.8.6-0ubuntu2
compizconfig-settings-manager 0.8.6-0ubuntu2
python-compizconfig 0.8.6-0ubuntu2

Extra packages:
fusion-icon 0.1.0-2
libdecoration0-dev 0.8.6-0ubuntu2

I believe you can get them from launchpad:
[https://launchpad.net/~compiz/+archive/ppa/+packages](https://launchpad.net/~compiz/+archive/ppa/+packages)

Download all in one directory then do:
dpkg --force-downgrade *.deb
or --force-all

Then mark the packages for hold (I used aptitude for that)

---

### Post by Bucic on 2011-06-01
Is it the case that installing Unity 2D gives 100% certainty that compiz will not be used or even loaded?

---

### Post by Copper Bezel on 2011-06-01
Not at all. It just means that you *can* use it with Metacity. But if you change the default window manager or run metacity --replace, then you're using Metacity and there's no Compiz involved (and likewise for Compiz.)

---

### Post by Bucic on 2011-06-01
> **Copper Bezel said:**
> Not at all. It just means that you *can* use it with Metacity. But if you change the default window manager or run metacity --replace, then you're using Metacity and there's no Compiz involved (and likewise for Compiz.)
So can I uninstall compiz after I install / login to Unity 2D?

---

