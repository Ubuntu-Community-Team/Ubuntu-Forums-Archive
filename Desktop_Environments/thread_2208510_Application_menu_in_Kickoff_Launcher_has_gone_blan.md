---
title: "Application menu in Kickoff Launcher has gone blank"
date: 2014-02-28
forum: Desktop Environments
---

### Post by Deborah_Anderson on 2014-02-28
I just installed Ubuntu 13.10.  I did apt-get install for all three of lubuntu-desktop, kubuntu-desktop, and xubuntu-desktop so I can decide which works best for me. KDE is Platform Version 4.11.5.

In Kubuntu, initially the Kickoff Application Launcher was fine.  The Application menu listed all the apps on the system.  At some point - and I don't know what I did that caused the change - when I clicked on Kickoff and slid to the Application menu, nothing was listed.  The menu area is completely blank white.

I'm looking for help to get the applications listed again, and any insight into what I did that caused the problem.  Here are more details.

The blank menu is in Application Launcher Style.  In Classic Menu Style, the pop-up menu shows entries for "Favorites", "Run Command..." and "Leave".  It doesn't list "Applications". 

When I right-click on the Kickoff icon, the pop-up menu has three items "Switch to Classic Menu [or Application Launcher] Style", "Application Launcher Settings", and "Panel Options". I think I remember that there used to be a fourth option, something about configuring the listed applications.  That one's no longer listed.

KDE Plasma Workspace and KDE/Openbox both show a blank screen. I don't remember which one I was running when the change occurred.

Based on a similar problem reported in 2009 ([https://www.kubuntuforums.net/showthread.php?40464-Menu-lost-application-icons-(Kickoff-and-Lancelot)](https://www.kubuntuforums.net/showthread.php?40464-Menu-lost-application-icons-(Kickoff-and-Lancelot)) I removed ~/.kde.  That is, I killed Plasma, used KRunner to start Dolphin, moved .kde to the trash, used KRunner to logout, then logged back in.  That didn't help.  The Kickoff Application menu is still blank.  Emptying the trash before logging out didn't help.

It seems that the .kde directory is recreated almost immediately after the old one is moved to the trash.  The following message is then displayed:
> Unable to save bookmarks in /home/deb/.kde/share/apps/kfileplaces/bookmarks.xml. Reported error was: Insufficient permissions in target directory.. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.


I have two areas of concern.

First, I'll appreciate any help I can get for recovering the Applications list.

Second, does anyone have any clues what I did that caused this problem? Is it bad to have all three desktop packages installed?

I saw similar behavior previously, with a different desktop (probably one of the Gnomes).  Makes me suspicious that I'm doing something in my poking around setting up panels, etc, that's causing problems.

At this point, it's still feasible to just start over with a clean install and apt-get's, but I don't want to stumble into this problem when I'm back at work.

Thanks for your help.

---

### Post by Deborah_Anderson on 2014-02-28
After taking time to write up the problem description, I realized I need to not wait, just go ahead and reinstall.

So how to solve the problem is no longer an issue.

However, any tips on what happened or how to avoid it in the future will be greatly appreciated.

I think I've got all the apps I need from Kubuntu.  I'm planning to not install the Gnome and Xubuntu desktop packages.  I'm hoping that will help.

Thanks anyway.

---

