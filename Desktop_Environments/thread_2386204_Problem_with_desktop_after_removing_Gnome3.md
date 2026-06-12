---
title: "Problem with desktop after removing Gnome3"
date: 2018-03-02
forum: Desktop Environments
---

### Post by tobcob on 2018-03-02
Hi everybody,
I'm new here so I hope this is the right place for this Thread.
I'm using Ubuntu 16.04 LTS and I've recently decide to try GNOME3, I tried to install it but when I restarted my laptop gnome wasn't working so well, so after looking around some blogs I tried to remove and install it again but the problem was the same.
So I decided to remove gnome3 and now the problem is that Unity is not the same as before: I can't have a desktop background, is completely black (but icons and the right click still work) and when I start my computer just before the lock screen the screen turns all white for 10/15 seconds and then it starts.
I tried to remove all the ppa that I've installed before but seems they're already removed, I tried to have a look at the tweak tools and I've discovered that if I turn off the icons on the desktop my background appears but I can't use the right click and nothing else, If I turn it on I can use the desktop but it is all black.

Could you help me to find a solution?

Thank you

---

### Post by again? on 2018-03-02
Did you use ppa-purge to purge the ppas where you installed gnome3 from?
Have a read ----> [GNOME3 PPA End of Life Announcement]("https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004229.html")

Both ppas have warnings.
> GNOME3
PPA description
Before upgrading your system to a new Ubuntu release (i.e. from Ubuntu 16.04 to 16.10), you should run 'ppa-purge ppa:gnome3-team/gnome3' first.

*** You need to run 'sudo apt-get dist-upgrade' to avoid problems. ***
Please read the output before entering 'Y' to make sure important packages won't be removed.

=== Bugs ===
Please use 'ubuntu-bug' to report bugs against packages in this PPA

=== End of Life ===
This PPA is no longer updated for releases older than Ubuntu 17.04. If you are using an older release, please ppa-purge this PPA and consider upgrading to a newer Ubuntu release.
Unless otherwise posted, updates will only be provided in this PPA for 7 months from the original release of the associated Ubuntu series.
[https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004229.html](https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004229.html)
> GNOME3 Staging
PPA description
This PPA will be used to test uploads before they are uploaded to the main archive for the coming Release.

=== *WARNING* ===
The packages here have been deemed not ready for general use, they have known bugs and/or regressions, sometimes of a critical nature. Mostly things should run smoothly but be prepared to use ppa-purge, when you encounter issues!

If they break your system, you get to keep both halves.

=== Installing ===
To use this PPA, you should enable the main GNOME3 PPA.

- You need to run 'sudo apt-get dist-upgrade' to avoid problems. Please read the output before entering 'Y' to make sure important packages won't be removed.

=== Removing ===
Use ppa-purge to remove this PPA. It is *particularly* important to do this before upgrading to a new release!

ppa-purge gnome3-team/gnome3-staging
ppa-purge gnome3-team/gnome3

=== Bugs ===
Please use 'ubuntu-bug' to report bugs against packages in this PPA

=== End of Life ===
This PPA is no longer updated for releases older than Ubuntu 17.10. If you are using an older release, please ppa-purge this PPA and consider upgrading to a newer Ubuntu release.
Unless otherwise posted, updates will only be provided in this PPA for 7 months from the original release of the associated Ubuntu series.
[https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004229.html](https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004229.html)

---

### Post by tobcob on 2018-03-02
I've done ppa-purge now and the problem with the desktop is gone, thank you! 
The white screen is still there but after 5 seconds goes away.

---

### Post by again? on 2018-03-02
OK...
Just a note, ppa-purge only works if the ppa is enabled.
> **tobcob said:**
> 
I tried to remove all the ppa that I've installed before but seems they're already removed


---

