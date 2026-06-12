---
title: "Howto upgrade firefox?"
date: 2006-03-01
forum: Desktop Environments
---

### Post by JohnnyWalker on 2006-03-01
I cant find out how to upgrade firefox. I tried an apt-get install firefox, which claimes that I am using the latest. I am using 1.07, which is far from latest.

Why is apt-get still not updated, this is a security issue?

---

### Post by FoxLogic on 2006-03-01
No, the repositories haven't been updated with the new version.  They wont ever be updated because Apparently the Dapper Drake release will have the newest one.  That being what I've heard.

If you really want to upgrade to the new version, I suggest using Automatix or search the Wiki page for the step by step tutorial.

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by manicka on 2006-03-01
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by JohnnyWalker on 2006-03-01
Ok, so it is possible to install firefox 1.5. Fine, but do you really think this is the way to go for user friendlyness, to have the most common application, the web browser, to be upgraded this way? Please note that this is not a feature upgrade only, but a security upgrade. 

I think it should be automatically upgraded, when selecting the package update function.

Please, note, I can manage this, but try to help pinning out what has to be done with ubuntu to be really smooth for ordinary users.

---

### Post by Tyr_7BE on 2006-03-01
Ordinary users won't want to upgrade their browser.  If anyone is looking seriously at firefox 1.5, and they know the need it SO BAD that they can't possibly wait until dapper, they'll probably know how to handle the install.  Ordinary users can wait until dapper.

---

### Post by pinguinus on 2006-03-02
This subject has been dealt with in at least a dozen threads already. Just search *firefox 1.5* to find more information about installing Firefox 1.5.

From one of the previous threads:
[I]"The other issue with upgrading to 1.5, is that you'll also have to get updates for every application that embeds Gecko. That includes Yelp, which is the Gnome Help Browser."
[/I]
So, for example the GNOME help browser used in Breezy would break and not work anymore if the gecko engine gets updated. 

Linux and Unix systems in general tend to follow the approach that common software like libraries shared by many applications are indeed shared and not included in the appliacations themselves which would make the packages bigger increasing bloat. The modular approach has its pros and cons. For example, if some library needs a security update, it only needs to be updated once, and then all apps using that library are fixed, instead of one needing to upgrade all those apps. However, this Firefox 1.5 issue is an example of the cons. Upgrading to Firefox 1.5 gets a bit more difficult as that means upgrading the gecko engine shared by many other applications too - so all those other applications would need to be upgraded too in order to guarantee them working.

However, like is described in [https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion") it is also possible to have both the standard older Firefox and install the newer version besides of it. Automatix seems to be an easy to use tool to install Firefox 1.5 too. Hey, by the way, why haven't anyone added also the Automatix method to the above guide yet?

As far as I know Ubuntu 6.04 Dapper Drake is getting quite stable already, so if you don't want to follow the various guides of installing Firefox 1.5 while using Breezy, it might be a good idea to just dist-upgrade the whole Ubuntu OS to Dapper - and get lots of other nice new things besides of Firefox 1.5.

(Another idea, if you like to be on the bleeding edge a bit more, with apps like Firefox, you might consider trying Debian testing or unstable besides/instead of Ubuntu's stable releases. In both the unstable and the testing branches of Debian apps are updated much more frequently than in Debian's or Ubuntu's stable releases. If you've used Ubuntu some time already, switching to Debian would not be not that difficult although configuration takes some more time.)

---

### Post by pinguinus on 2006-03-02
Ok, just tried Automatix for the first time too... Looks like quite a handy tool :) I'm writing this now in the newest Firefox 1.5.0.1 while using Breezy so the Automatix installation went fine.

Installing Firefox 1.5 with Automatix is quite easy, and could be perhaps described as the recommended way of installing Firefox 1.5 in Breezy. It also sems to make backups of you previous configurations like bookmarks, so don't panic if you notice that your old bookmarks are gone after using Automatix to install the new Firefox.

One thing worth noting is also that Automatix wants to overwrite your old  sources.list file with its own, but here too it made a backup of my original apt sources.list file, so no problemo.

More information regarding Automatix:
[http://www.ubuntuforums.org/showthread.php?t=114251]("http://www.ubuntuforums.org/showthread.php?t=114251")
[http://ubuntuforums.org/showthread.php?t=80295&highlight=automatix]("http://ubuntuforums.org/showthread.php?t=80295&highlight=automatix")

---

### Post by tagg3rx on 2006-03-02
> but do you really think this is the way to go for user friendlyness, to have the most common application, the web browser, to be upgraded this way? Please note that this is not a feature upgrade only, but a security upgrade.

This is exactly why automatix should be the 1st thing anyone installs.

Many threads read to this extent 

think of it as Ubuntu SP1

---

### Post by JohnnyWalker on 2006-03-03
"t might be a good idea to just dist-upgrade the whole Ubuntu OS to Dapper"

Is this done by downloading a full iso, burning it to CD and install, or is there another way, like downloading neccesary packages from a repository automatically?

---

### Post by GeirG on 2006-03-03
I'm quite sure you can edit /etc/apt/sources.list and replace "breezy" with "dapper", then run apt-get update && apt-get upgrade...

... however, I'm not sure that is necessarily a good thing to do :-)

There is a lot of activity in the Dapper repository, and I have no idea about the stability. We are closing in on the release of Dapper, so things are probably getting good, but I wouldn't do this on a system of any importance as I don't think you have any guarantees against breakage.

Good luck :-)

---

### Post by JohnnyWalker on 2006-03-04
Ok, if we are close to a release, I can wait a while.

Nice to know that there is a convenient way of upgrading, when it is available.

Would'nt it be a good idea to have this repository as an option in the "synoptic package manager"'s repository choises? Whit a dialog saying, that this type of upgrade will take quite some time, when selected. To minimize the effort of every user, especially new users.

---

### Post by pinguinus on 2006-03-04
Yeah, like GeirG said, I'd recommend using Automatix instead of upgrading the whole OS to Dapper, especially if it is only Firefox 1.5 what you want. (Sorry for suggesting upgrading to Dapper, i.e. choosing a complicated solution to a simple propblem.) Read the Automatix page [http://www.ubuntuforums.org/showthread.php?t=114251]("http://www.ubuntuforums.org/showthread.php?t=114251") and after that using Automatix is quite easy.

Oh, here's one more good Automatix page, about removing software installed by Automatix:
[http://ubuntuforums.org/showthread.php?t=90797]("http://ubuntuforums.org/showthread.php?t=90797")
In the case of Firefox 1.5, removing it and restoring the original settings of the older Firefox is not as easy as just apt-get remove firefox which is why I mention that page here too.

---

