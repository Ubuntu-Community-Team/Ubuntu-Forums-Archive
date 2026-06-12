---
title: "Can't launch Konsole anymore?"
date: 2012-10-26
forum: Desktop Environments
---

### Post by christian.convey on 2012-10-26
I just did a fresh install of Ubuntu 12.10 64-bit edition.  I also installed the Gnome Classic desktop, as well as the KDE-based editor, "konsole".

When I click on the menu icon for Kate, I get a dialog saying this: "Failed to change to directory '$HOME' (No such file or directory)", and Kate fails to launch.

I'm still able to launch other KDE-based apps, such as Kile, from the menu without a problem.

I'm also able to launch 'kate' from a gnome-terminal command line.

Any idea what's going on?

---

### Post by Program-mist on 2012-11-29
Same situation: Ubuntu 12.10 x64, Unity,
Can't run Konsole by clicking icon in Unity panel.
Pressing F2 in Krusader is successfuly running it.
On another notebook: Ubuntu 12.10 x86, Cairo-Dock (Gnome),
konsole works fine.

Where is solution?

---

### Post by Program-mist on 2012-12-08
I found solution myself.

Open (as sudo) /usr/share/applications/kde4/konsole.desktop file.
Find line: Path=$HOME
I change it to my home dir path.
Save file. It works now.

Useful link.
[https://bugs.launchpad.net/unity/+bug/1063630](https://bugs.launchpad.net/unity/+bug/1063630)

---

