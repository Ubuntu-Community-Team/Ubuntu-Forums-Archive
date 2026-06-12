---
title: "Help! KDE 4.2 screwed up my system!"
date: 2009-01-28
forum: Desktop Environments
---

### Post by lodp on 2009-01-28
Hi,

I just upgraded my Kubuntu Intrepid box to KDE 4.2, and now I'm stuck with a dysfunctional system. It boots normal as far as the KDM login screen, but after I log in, I'm stuck an empty background image and a mouse cursor.

When installing, I followed the instructions for 8.10 in the release note kubuntu.org: I added those launchpad repositories and the gpg-key, ran an Adept Manager upgrade, which took a while. Towards the end of the process I was asked to supply a new MySQL root password, and whether I wanted to keep or replace my old kdmrc file (I chose to replace it). After the upgrade was done I tried to log out, but that wouldn't work. So I hit ctrl+alt+backspace, and the Alt+E to restart X. And that's where I now: I can't log in to KDE anymore. I don't have gnome installed either.

I can select console login and get a command prompt, but I have no clue where to go from here. Can I remove those new repositories, reinstall kubuntu-desktop and get KDE 4.1.something back?


EDIT: Solved. I ran and apt-get upgrade from the command line, which installed kdebase-workspace-data. Then I installed kubuntu-desktop, which also installed kdebase-workspace-bin, after which KDE 4.2 started normally. 

This is pretty serious. If I hadn't had my laptop as a backup and found that tip with installing kubuntu-desktop somewhere, I would probably have had to re-install my entire system.

I just went to bugs.kde.org to report this, and their database server was down because of too many connections :)

---

### Post by ltmon on 2009-01-28
It's a packaging bug in any case, so you should report it to the kubuntu developers on [http://bugs.launchpad.net](http://bugs.launchpad.net), rather than directly to the KDE developers who are not responsible in this case.

It looks like this was possibly a case of bad luck and timing, where you upgraded before the upload of new packages to the repository was completed.

---

### Post by lodp on 2009-01-28
Thank you, I'll go and report it at launchpad then..

As for the timing -- do you think that this is likely (since I upgraded more than 24h after the initial release)?

---

### Post by arcanus on 2009-01-29
Yes, it might happen. I have seen a >48hrs sync delay on some mirrors, so it depends on your mirror.

---

