---
title: "playdeb.net issues"
date: 2010-04-16
forum: Gaming &amp; Leisure
---

### Post by Rhetoric Camel on 2010-04-16
I have tried to download a couple games from playdeb.net and I keep getting this everytime I click "download"

> W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg)  Could not resolve 'archive.ubuntustudio.org'

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntustudio.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.


any idea why I get this and how to fix it? Sorry if this is in the wrong section. Figured I'm having trouble with installing/download a game so I should post in the gaming section.

---

### Post by hikaricore on 2010-04-16
Uhh yea it appears that you can't connect to archive.ubuntustudio.org and this has nothing to do with playdeb.  :p
It's all written out there in plain english.  Check your sources and disable that one if it's down or gone for the time being.

---

### Post by Rhetoric Camel on 2010-04-16
thank you, sorry I'm a bit of a noob with the whole ubuntu thing, didn't realize it was a thing I had to uncheck in the sources. Did it and the message doesn't pop up... says it can't find what I'm trying to download from paydeb but I'm just assuming that it's no longer there or doesn't exist. 

Thanks for the help

---

### Post by myromance123 on 2010-04-17
Just a question, have you installed Playdeb's package beforehand?
 You need it to be able to download the games from PlayDeb.

If you haven't yet, go here:[http://www.playdeb.net/updates/Ubuntu/all#how_to_install]("http://www.playdeb.net/updates/Ubuntu/all#how_to_install")

 Do number 1 :)
Hopefully that helps.
If you've already done it, then you can forget about what I said :P

---

### Post by jkxx on 2010-04-17
Playdeb appears to be broken on 10.04 at least at the moment. Attempting to add the repo causes my kpackagekit to just hang. I'll give it a while and maybe post an update later.

:popcorn:

---

### Post by myromance123 on 2010-04-17
Kpackagekit means you're using Kubuntu?
 I'm using just Ubuntu 10.04 Beta 2, so far no problems with playdeb.net.
Just tried downloading 0 A.D yesterday, it works :)

Just letting you know. :popcorn:

---

### Post by lamego on 2010-04-17
It must be a problem kpackagekit, even if there was a problem with the getdeb archive the application should not hang...

---

### Post by hikaricore on 2010-04-17
Kde's package management tools have always been lacking.
Just use synaptic and be done with it.  ^_^

---

### Post by jkxx on 2010-04-18
I might try Synaptic but I've learned not to mess with the package system. Don't want another busted partition :)

Yes, I don't use/like gnome so rely on the KDE tools instead. So far the instructions don't work on Kubuntu and I just get errors when trying to install anything (Firefox not recognizing the apt handler, etc)

I can still install most of those games just by looking them up although I'm finding most of them have either graphical or sound problems, although that's a different issue.

Anyway, for those having trouble with the instructions and using Kubuntu: if you really want to try a particular game, try searching for that game in KPackageKit. Chances are it will be there and you'll be able to install it.

---

### Post by hikaricore on 2010-04-18
To use the click based system on playdeb you need to install the proper package.
This is covered in the howto on their site.

The sound/video issues are likely a problem with your system.

---

### Post by HHx66 on 2010-04-18
It's working fine for me in Synaptic, I haven't tried KPackageKit, I don't like it (even though I much prefer every other aspect of Kubuntu over Ubuntu)

---

### Post by Rhetoric Camel on 2010-04-18
> **myromance123 said:**
> Just a question, have you installed Playdeb's package beforehand?
 You need it to be able to download the games from PlayDeb.

If you haven't yet, go here:[http://www.playdeb.net/updates/Ubuntu/all#how_to_install]("http://www.playdeb.net/updates/Ubuntu/all#how_to_install")

 Do number 1 :)
Hopefully that helps.
If you've already done it, then you can forget about what I said :P

I have installed it, made sure it was for Jaunty (that's what I'm using) I can get games but unfortunately the game I'm trying to get is not available (irrlamb)

---

### Post by Rhetoric Camel on 2010-04-19
> **myromance123 said:**
> Just a question, have you installed Playdeb's package beforehand?
 You need it to be able to download the games from PlayDeb.

If you haven't yet, go here:[http://www.playdeb.net/updates/Ubuntu/all#how_to_install]("http://www.playdeb.net/updates/Ubuntu/all#how_to_install")

 Do number 1 :)
Hopefully that helps.
If you've already done it, then you can forget about what I said :P

I did that and I've gotten further, but now I'm getting

> Can not install '0ad' (E:Unable to correct problems, you have held broken packages.)

When I try to download 0ad from playdeb.

 when I try to install it from synaptic I get

> **Could not mark all packages for installation or upgrade**
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

0ad:
 Depends: libboost-filesystem1.38.0 (>=1.38.0-1) but it is not installable
 Depends: libboost-signals1.38.0 (>=1.38.0-1) but it is not installable
 Depends: libboost-system1.38.0 (>=1.38.0-1) but it is not installable
 Depends: libenet2  but it is not installable
  Depends: libstdc++6 (>=4.4.0) but 4.3.3-5ubuntu4 is to be installed
  Depends: libwxbase2.8-0 (>=2.8.10.1) but 2.8.9.1-0ubuntu6 is to be installed
  Depends: libwxgtk2.8-0 (>=2.8.10.1) but 2.8.9.1-0ubuntu6 is to be installed
  Depends: libxml2 (>=2.7.4) but 2.6.32.dfsg-5ubuntu4.2 is to be installed



although I was able to download and install Phun. I'd like to get irrlamb but that can't be found when I click it.

---

### Post by myromance123 on 2010-04-19
Hmmm broken packages... I've been through something like this in the past.
Let me try and recall..

 In the past when it told me I had broken packages or dependencies, I would open up a terminal and do this:
```
sudo dpkg --configure -a
```

 That normally fixed it all for me. Would you mind giving it a try?

If you would like to see what packages are broken, open up Synaptic Package manager. Then on the bottom left, click Custom Filters.
 Right above it, new options list will be available. Click on 'Broken'.
That should show you whats broken.

 I'm glad I'm helping you move forward with this issue, I hope it can be resolved :)

EDIT: Don't install 0 a.d from Synaptic, its never worked for me today and in the past. If others know how, let them share their knowledge.

---

### Post by jkxx on 2010-04-19
myromance123, thanks for the dpkg tip! Thanks to that I can install packages again. I had to remove the playdeb repo link to get there though so I'll hold off on that for a while till it works better in Kubuntu.

hikaricore, I'm fairly certain the problems are in the native gtk apps rather than with my audio or video config. I have no problem with sound in KDE or Wine and likewise video is working well elsewhere. The wine ports of some of the same emulators work without problems as well (snes9x, zsnesw, gens32, nestopia are some of the ones I've tried).

I might play with those a bit and try to figure out if there's a particular bug involved.

---

### Post by myromance123 on 2010-04-19
I'm glad I was of assistance to you jkxx :D

---

