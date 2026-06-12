---
title: "KDE 3.5.4 toolbar won't show open applications"
date: 2006-08-02
forum: Desktop Environments
---

### Post by seedsgrow on 2006-08-02
I'm not usually so impatient, but I upgraded KDE to version 3.5.4 today, the first day it was available.  Almost everything seems to be working quite well.  This new version does indeed, as the release notes say, offer better USB device support, which is what I was after.  The only problem I've noticed so far is that icons for open applications no longer show on the taskbar, so to get a look at minimized windows, I must middle click on an empty space in the desktop.  That's a bit inconvenient.  I have checked the panel configuration options, and they are set to display the icons of open applications on the toolbar.  I have restarted KDE and rebooted, but the icons still refuse to appear.  All of the other panel icons, those for applets and those for quick launch, display with no problem.  Is this a bug?  Anyone with suggestions on what the problem might be or how I might fix it?

Tom

Edit:
Since posting this I have found that the taskbar is now an optional applet. I just needed to add it to the panel for it to work properly.

---

### Post by wieman01 on 2006-08-02
So has this solved your problem? Just curious because I was thinking whether I should upgrade or not.

Would you recommend an uprade in general? The improved USB support sounds appealing to me.

---

### Post by Jucato on 2006-08-02
Don't upgrade yet, unless you know how or are willing to workaround the bugs.

The "unofficial" official announcement (unofficial because it has not be posted on the main Kubuntu web page yet):
[http://kubuntu.org/announcements/kde-354.php](http://kubuntu.org/announcements/kde-354.php)

---

### Post by wieman01 on 2006-08-02
Ok, I'll just wait until it's in the repository. Thank again, mate.

---

### Post by Jucato on 2006-08-02
It won't be in the repository. Updates to KDE, Amarok, and KOffice, for some reason, are never added to the main repositories. You have to add the special official Kubuntu repositories made just for them.

---

### Post by wieman01 on 2006-08-03
Ok, if anybody is interested this the repository for Kubuntu & Amarok:

> # kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

There is a generator tool which you can use should you need additional repositories for 3rd party software, etc.:

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by Jucato on 2006-08-03
As much as it is nice to have the kde-latest and amarok-lates (you forgot koffice-latest), I think there is a disadvantage with having the *-latest repositories permanently in your sources.list. Once the system detects that updates are available, the normal compulsion would be to upgrade, without reading the announcement. In this case, the upgrade could be fatal.

Luckily the kde-latest repository doesn't isn't updated to KDE 3.5.4 yet. I guess they would only update that particular repository it if it's absolutely safe to upgrade.

Anyway, just my opinion. Nothing official. :D

---

### Post by wieman01 on 2006-08-03
I agree with you. Although one might think that updates/upgrades end up in the repository only AFTER proper testing, it's a risk.

Nonetheless security updates are necessary once in a while...

KOfice... Yes, I did not include it because I am not using it. But anybody reading this: You play around with the generator tool, it has all you need. BUT AT YOUR OWN RISK, I shall add. :-)

---

### Post by Jucato on 2006-08-03
KDE 3.5.4 is **officially** available in Kubuntu.

[http://www.kubuntu.org](http://www.kubuntu.org)

Since it has been added to the front page, and RSS feeds have been sent, it's presumably safe to upgrade now.

---

### Post by the-linux-guy on 2006-08-03
Be carefull to upgrade your system to 3.5.4 at this time. I did it yesterday, the upgrade went smooth and all; but after a new login as user I noticed that all my KDE desktop was screwed up ! No KDE start-menu, no applets loading, no icons on the taskbar indeed ;-), no logout button and... no WLAN showing up in the KWifiManager... :-(

I was glad that I made a system wide backup before updating (allways doing that) so I could restore my KDE system in just minutes (or my wife would have me skinned alive ;-) )

So guys, I sure DO NOT upgrade at this time...
Kind regards,

Eddy

---

### Post by Jucato on 2006-08-03
That was because, until I posted my last post, it was **not** recommended to upgrade to KDE 3.5.4, even if the packages were already available.

But now as of 03:00 UTC, it is "officially" released, and the warnings have been removed.

---

### Post by wieman01 on 2006-08-03
Ok, great to hear that. Thank you. But I took your advice, I won't upgrade until I really need to. Why change a running system?! :-)

---

### Post by Jucato on 2006-08-03
> **wieman01 said:**
> Ok, great to hear that. Thank you. But I took your advice, I won't upgrade until I really need to. Why change a running system?! :-)

Actually my advice was: don't upgrade until the Kubuntu devs give the green light (which is what they did when they officially posted they posted the official announcement in the main Kubuntu page).

Why change a running system? KDE 3.5.4 fixes some bugs present/found in KDE 3.5.3, so it **might** be worth the upgrade.

---

### Post by wieman01 on 2006-08-03
Alright, alright... On the same page. I'll be a bit more precise next time. :D

---

