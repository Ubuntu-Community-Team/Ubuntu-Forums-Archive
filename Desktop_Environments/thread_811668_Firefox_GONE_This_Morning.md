---
title: "Firefox GONE This Morning"
date: 2008-05-29
forum: Desktop Environments
---

### Post by user1234 on 2008-05-29
This morning I ran:
```
sudo apt-get update; sudo apt-get upgrade
```
and FireFox vanished.  Somewhat stunned, I checked, yep, totally gone.  So, I run sudo apt-get install firefox and got:
```
The following packages have unmet dependencies:
  firefox-3.0: Depends: xulrunner-1.9 (< 1.9~b6~) but 1.9~rc1+nobinonly-0ubuntu1~8.04.1 is to be installed
```
Brilliant, my single most used app is now gone and I have some conflict with a package I had to look up to see what was, xulrunner.  I'm guessing somewhere in my sources, someone had packaged xulrunner in a way that has screwed me up.

One would think an RC1 is newer than a B6, but aparently firefox isn't happy.  Any ideas?

EDIT: Couple apt-get updates later (30 minutes) and it is installing...  So, the mirror seems to have been updated, and it's fixed.

---

### Post by bucky100771 on 2008-05-29
Same here....Also my gnome is locked up and my Adept doesn't seem to let the FF reinstall.  I went to the mothership at firefox.com, but cannot make out how to install the linux version.  I was never handy at compiling....and I sure as hell am now not hardy either.

---

### Post by tsmgroup2 on 2008-05-29
Hi, Fellas.

I did a (partial upgrade) thru the update manager on one of my i386 machines with the 8.04 version and my firefox disappeared too.  Same dependency problems as yours with that xulrunner 1.9.  

I believe the developers are working on it and I wouldn't doubt the amd64 machines already having a firefox deadlink issue is related to this problem as well seeing how these two machines of mine after going thru a (partial upgrade) after using the update manager both have relative problems.

Sometimes, it pays to use old reliable versions and have backup disks for say 7.10 until such problems as these are resolved.

I keep forgetting, I can always load up and use the previous version on my other machines as long as it is and 'upgrade' and not a 'fresh install'.  

Hope we all can soon have these resolved.
Just go to your applications>internet>firefox 2 for now and it should run alright for ya
That's what I found at least...

Thanks to all for your input...
:guitar:

---

### Post by DJ_Peng on 2008-05-29
All you have to do is extract it to a location (I simply extract it to my home folder) and then run path.to.firefox\firefox from the terminal. You will need to copy your plugins from the old location to the new one, but that isn't all that difficult to do. You could also change your launchers to use that location. 

One perk for using Mozilla's code: When they release updates they'll be available to you a lot faster (a couple days at least) than you'd see getting it from the repos.

---

### Post by BlueSkyNIS on 2008-05-29
From: [http://ubuntuforums.org/showthread.php?t=811670]("http://ubuntuforums.org/showthread.php?t=811670")

> [QUOTE]
Quote:
Originally Posted by Riffer View Post
Just had an update and it removed FF3. I know theres been a lot of trouble with FF3 but is it so much that they needed to remove it?
There is no such thing as removing it, Firefox3 is still being built which is why there are dependency errors. But Firefox3 has now reached the Sri Lankan server, so just update the sources list, that should allow you to reinstall/update Firefox3 properly.[/QUOTE]

So update repositories and try again installing FF


Cheers

---

### Post by Backharlow on 2008-06-01
see this bug report [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/235769]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/235769")
And the solution I had to use:
"By using the Synaptic Package manager, one can use the Force Version tool (under "Packages") to set xulrunner back from 1.9rc1 to 1.9b5 or earlier. After doing this, FF3.0 can be reinstalled."
This works. I don't know what issues it may cause down the road though.

---

### Post by Bubba64 on 2008-06-02
Launchpad has released an upgrade of FF3 rc1 today try running update and upgrade, mine installed fine on two different computers. I haven' read the launchpad link yet though. I am assuming that those of you that are having problems had updated via launchpad to rc1 and this is in the 3rd party install of software sources.
[http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/](http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/)
I got a update of xulrunner for rc2 the latest launchpad upgrade, but xulrunner is shut off in FF add ons I enabled xulrunner rc2 no problems.

---

### Post by tsmgroup2 on 2008-08-25
> **tsmgroup2 said:**
> Hi, Fellas.

I did a (partial upgrade) thru the update manager on one of my i386 machines with the 8.04 version and my firefox disappeared too.  Same dependency problems as yours with that xulrunner 1.9.  

I believe the developers are working on it and I wouldn't doubt the amd64 machines already having a firefox deadlink issue is related to this problem as well seeing how these two machines of mine after going thru a (partial upgrade) after using the update manager both have relative problems.

Sometimes, it pays to use old reliable versions and have backup disks for say 7.10 until such problems as these are resolved.

I keep forgetting, I can always load up and use the previous version on my other machines as long as it is and 'upgrade' and not a 'fresh install'.  

Hope we all can soon have these resolved.
Just go to your applications>internet>firefox 2 for now and it should run alright for ya
That's what I found at least...

Thanks to all for your input...
:guitar:

I finally did a complete re-install with one of the new ubuntu 8.04.1 install cds and success!!  No more problems with Firefox 3.0 at all
Just be careful what plugins you use, too many and it seems to get a little twitchy.

I am still having problems getting one of the Samsung Writemaster DVD burners to work on this version though, see my other thread..

Thanks everyone!

---

