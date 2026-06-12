---
title: "Plasmoids Removing Themselves"
date: 2009-03-21
forum: Desktop Environments
---

### Post by Unanimated on 2009-03-21
Yesterday, I installed digiKam from the repos to get a video off of my digital camera and put it on Youtube. This deleted the default image viewer, which I thought was fine, until my screensaver kicked in. I have some widgets on my screensaver - the digital clock, incoming messages, the weather, and the calculator. All of them except the digital clock showed an error saying they couldn't find the plasmoid. This morning, when I logged in, it showed me my desktop. I have the folder viewer, disk space management, dictionary, and notepad plasmoids on my desktop. The dictionary and notepad plasmoids both displayed error messages saying they couldn't find the plasmoid. Also, on my taskbar, the Show Dashboard plasmoid was replaced with a red X, and when I moved over it, it said that it couldn't find the plasmoid. What happened?

By the way, the video is [here]("http://www.youtube.com/watch?v=ne15Tp3t-kw"), if anyone wants to watch it.

---

### Post by krazyd on 2009-03-22
Installing digikam deleted gwenview? that shouldn't have happened - I've got both installed side-by-side here. Try reinstalling gwenview.

---

### Post by Unanimated on 2009-03-22
Apparently they can't be side-by-side on mine. Here's the terminal output:

```
sam@sam-desktop:~$ sudo apt-get install gwenview
[sudo] password for sam:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdeplasma-addons-data libkexiv2-3 mpg123 libmpg123-0 libkdcraw3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libkipi6
The following packages will be REMOVED:
  digikam kipi-plugins libkipi-common libkipi0
The following NEW packages will be installed:
  gwenview libkipi6
0 upgraded, 2 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B/1361kB of archives.
After this operation, 35.3MB disk space will be freed.
Do you want to continue [Y/n]?

```

I'm using Kubuntu 8.10, if that helps.

---

### Post by txcrackers on 2009-03-23
digikam --> libkipi0
gwenview --> libkipi6

That appears to be the answer - conflicting versions of a library. It seems to indicate that the repo version of digikam is out of step with the rest of the KDE/Qt applications installed.

You could just use a mini-card reader for the disk in the camera - even the one built into my wife's POS Compaq works great in Ubuntu.

---

