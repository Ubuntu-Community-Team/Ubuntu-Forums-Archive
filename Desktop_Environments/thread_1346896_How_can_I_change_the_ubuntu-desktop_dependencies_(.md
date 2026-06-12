---
title: "How can I change the ubuntu-desktop dependencies? (pulseaudio problems - 9.04)"
date: 2009-12-05
forum: Desktop Environments
---

### Post by evan2645 on 2009-12-05
Hello. I've done quite a bit of googling on this issue, and there seems to be a googol ways that people are doing this, however I have not found any of the methods to my satisfaction, so I am making this post to see what the Ubuntu community thinks...

I recently purged pulseaudio from my system in a desperate attempt to resolve some pretty nasty system stability issues. I was aware that ubuntu-desktop depends on it, but seeing as how everything seems to work just fine after its removal, I'm not quite sure why it does... Anyhow, apt is effectively broken cause it yells at me about this missing dependency every time I try to do something (not to mention the ugly red icon it gives in my system tray), so I would like to somehow edit the dependency list of the ubuntu-desktop metapackage. I came across this
[http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

However, I hate to go through this whole process just to have it wiped out on the next system update... is this the best method to resolve the issue I am seeing? I suppose I could remove the package entirely, but I'd like to avoid that if possible since I have read this can lead to other issues.

I also found /var/lib/dpkg/status and proceeded to edit the dependency list for ubuntu-desktop to remove pulseaudio, however that didnt seem to work... but I haven't rebooted since then either so maybe that is an issue.

I saw the excellent tutorial on disabling pulseaudio, however I want it completely purged - at least in the meantime - to definitively say whether or not it is the cause of these stability issues... ANY/ALL input is appreciated! Thanks guys.

---

### Post by seeker5528 on 2009-12-05
The best option is to remove the ubuntu-desktop metapackage.

If you are sticking with the stable release, the list of things it pulls in is not likely to change.

Later, Seeker

---

### Post by Shazaam on 2009-12-05
ubuntu-desktop is a meta-package. It is safe to uninstall but will need to be reinstalled if you want to upgrade say Karmic Koala to Lucid Lynx.

"What is a meta-package? Is it safe to remove the ubuntu-desktop package?

A meta-package is a package that doesn't contain applications within itself, but simply depends upon particular versions of other packages, so that when it is installed, it drags all of them in too. The package manager uses it to know which particular packages to install. For example, the ubuntu-desktop metapackage installs the full GNOME desktop environment, with all the other packages that are in a default Ubuntu install. The existence of meta-packages makes it very easy to install other Ubuntu derivatives on your desktop; see below for more information.
It is technically just fine to remove a meta-package, if required, and this shouldn't necessarily cause any problems. However, it is strongly recommended that you reinstall that package if you decide to manually upgrade to another version of Ubuntu. The package manager requires those packages to be installed for it to successfully perform the upgrade".

From here...
[https://help.ubuntu.com/community/CommonQuestions#Meta-packages:%20ubuntu-desktop](https://help.ubuntu.com/community/CommonQuestions#Meta-packages:%20ubuntu-desktop)

---

### Post by evan2645 on 2009-12-07
Done. No problems encountered. Thanks for the advice.... unfortunately pulseaudio seems to not have been the cause of the stability problems :(

I know this should prolly be another thread, but does anyone here know of a deamonized utility that will log process statistics in realtime - similar to window's perfmon? I think there is may be blocking io going on somewhere...

Anyways, thanks for your help guys. I'll mark the post as solved in the next day or so.

---

