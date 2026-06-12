---
title: "kcontrol not saving changes"
date: 2009-04-22
forum: Desktop Environments
---

### Post by r.stiltskin on 2009-04-22
I am using gnome desktop (in hardy) but like to use a few kde apps, especially kate, kile, konqueror, konsole and k3b.  I have been trying (unsuccessfully) to change the system notification sounds used by kate.  But when I make changes to the event sounds in kcontrol, the changes have no effect and none of my changes are saved.

I assume my changes should be saved in .kde/share/config/kdeglobals or .kde/share/config/kcontrolrc?  Those files do change if I test-play a sound in kcontrol, but the only change is to update the "Recent Files" section.  If I make changes to the actual settings, by, for example, deselecting "Play a sound", the config files are not touched at all.

I have installed kate, kcontrol, kdebase-bin-kde3, kdebase-data, kdebase-kio,plugins, kdelibs-4c2a, kdelibs-data, kdesktop, kfind, kicker, konq-plugins, konqueror, konqueror-nsplugins, konsole.  All of these are version 4:3.5.10-0ubuntu1, all installed by Synaptic or apt-get so as far as I can tell all dependencies are satisfied.  (kile and k3b have different version numbers but that seems irrelevant -- they are both the latest versions & work correctly.)

I suppose I could manually change the sound files on disk, but I was hoping for a more elegant solution...

---

