---
title: "Desktop Search"
date: 2005-08-09
forum: Desktop Environments
---

### Post by Olrich on 2005-08-09
Hello all.  I was wondering if there was any application available for Ubuntu that has similar capabilities to the popular desktop search applications such as the Yahoo or MSN desktop searches.  I have tried using the default search utility that is installed with Gnome but I have seem to have dodgy results at best.  Thanks for any recommendations.

---

### Post by Stormy Eyes on 2005-08-09
[QUOTE=Olrich]Hello all.  I was wondering if there was any application available for Ubuntu that has similar capabilities to the popular desktop search applications such as the Yahoo or MSN desktop searches.  I have tried using the default search utility that is installed with Gnome but I have seem to have dodgy results at best.  Thanks for any recommendations.[/QUOTE]

There's a tool called Beagle currently in development that will be in the next Ubuntu release.

---

### Post by varunus on 2005-08-09
Here's how to install Beagle in Ubuntu Hoary:

[http://www.beaglewiki.org/index.php/UbuntuInstall](http://www.beaglewiki.org/index.php/UbuntuInstall)

---

### Post by Olrich on 2005-08-09
Thanks for the reply, this looks great.  But, I can't seem to get the Ubuntu backports repositories working.  No matter which mirror I use, when it tries to retrieve the listing it fails.  All the other ubuntu repositories work just fine.  I can enter the url of the repository and browse the files just fine.  But apt-get does not want to get a listing from those servers.  I suppose it would be possible to manually search through and download the .deb files and install, but this seems excessive.  Anyone know a solution to this?

---

### Post by varunus on 2005-08-09
What error message do you get exactly when you add a backports repo and reload packages in Synaptic?

---

### Post by Olrich on 2005-08-09
While it is downloading the repositories it displays a failed next to the backport ones.  After all the repositories are downloaded this message comes up.

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

Below this it lists all the urls for the whichover backports mirror I happen to be trying.

---

### Post by varunus on 2005-08-09
Have you tried multiple backports mirrors?  This is really weird...Maybe post over in the backports section of the forum, see if someone else has had/fixed this problem?  Are you sure you added the backports repo properly in your sources.list?

---

### Post by Olrich on 2005-08-09
This would be the correct way to add it, right?

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted

Thanks for the reply.

---

### Post by varunus on 2005-08-10
That looks correct to me...no idea why it isn't working...Sorry.

---

