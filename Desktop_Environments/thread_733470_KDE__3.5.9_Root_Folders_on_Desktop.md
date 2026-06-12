---
title: "KDE  3.5.9 Root Folders on Desktop"
date: 2008-03-23
forum: Desktop Environments
---

### Post by soulfly7x on 2008-03-23
I'm running Kubuntu Gutsy (7.10) on an AMD64 laptop. I followed the instructions for going to KDE 3.5.9
[http://kubuntu.org/announcements/kde-359.php](http://kubuntu.org/announcements/kde-359.php)

When I logged back in, I noticed that my Root folders were on the desktop. Browsing Dolphin or Konqueror shows that everything is in the right place. It's the Desktop itself that is wrong. 

Here you can see [a screenshot]("http://linux.radioactiveliberty.com/wp-content/uploads/2008/root-on-desktop.png") of the actual desktop files next to the desktop files in Dolphin.

I opened kcontrol and went to System Administration> Paths, and it showed that the Desktop path was set to / 
so was the Documents path.

I changed the Desktop path to */home/mike/Desktop/* and the Documents path to [i]/home/mike[\i]
When I clicked "apply" it asked if i wanted to move files from / to the new desktop location, but I didn't want to do that. They are the root folders. That's the whole point. I don't want them on my desktop. I want my desktop on my desktop.

I won't move them anyway, because they are root permissions. The paths have been changed to the correct paths, I logged out and...

Nothing. The root directory still shows on my desktop. 

As far as I can tell, everything else is functioning correctly. I have access to my desktop files through the file browser. I just want my desktop back. Any suggestions.

---

### Post by 162019444 on 2008-03-23
Have changed my profile  image, to have a look at the new one.

---

### Post by nicoladinisio on 2008-05-03
I have experienced the same problem when updating from Kubuntu 7.10 (gutsy) to Kubuntu 8.04 (hardy).

I have also checked the file .kde/share/config/kdeglobals, setting

Desktop=$HOME/Desktop

or

Desktop=/home/fabiana/Desktop

or

Desktop=/home/fabiana/Desktop/

under the section [ Paths ] but nothing happened, the KDE desktop remained set to the root folder (/).

Still investigating ....

/Nicola

---

### Post by nicoladinisio on 2008-05-06
Today (2008-05-06) the Adept notifier, notified me of a bunch of new updates available for my Kubuntu 8.04. Many of them were KDE releated, I applied them and the problem disappeared.
Now my desktop is back to normal and does not point to the root (/) folder anymore.
So my suggestion is to update your distro and get the latest patches now.

/Nicola

---

### Post by jklasdf on 2008-05-11
I am still having this bug with the latest updates. It seems that the recommendation at the bottom of [https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/174532]("https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/174532") fixes the problem.

---

