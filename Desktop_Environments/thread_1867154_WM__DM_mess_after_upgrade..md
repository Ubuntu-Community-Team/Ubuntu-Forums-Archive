---
title: "WM / DM mess after upgrade."
date: 2011-10-22
forum: Desktop Environments
---

### Post by xvan on 2011-10-22
Before upgrading I tired gnome shell in natty. There was were things went wrong... I installed gnome-shell but the shell never showed, and killed all my gnome themes.

So instead of fixing it, tried to upgrade. But several packages couldn't be configured.

I ended up without wireless driver, without X, and with lightdm crashing my system on startup. I fixed the first and replaced lightdm with gdm.

Then I couldn't use synaptic  nor apt, because of some dependencies issues in gnome, unity and xorg. The packages were old and couldn't be updated nor removed with any tool but aptitude.

So I purged gnome unity, compiz and  xorg conflicting packages, and  reinstalled them.

Now I find myself:

1)Without automatic DM... have to launch gdm myself, How do I fix this?
2)Without Unity: Unity is installed, but gdm says [Failed to load session "ubuntu"].
3)Without gnome-shell: Gnome shell in installed, but when I log to gnome, I end up with a nautilus desktop, without gnome panels.

gnome-classic (session fallback works fine).
I ended with a debian grub2 bootsplash.

Purging and reinstalling doesn't fix any of this issues.

---

### Post by xvan on 2011-10-22
> 1)Without automatic DM... have to launch gdm myself, How do I fix this?Stupid aptitude left my /et/X11/default-display-manager using lightdm. even when it wasn't installed.

> 2)Without Unity: Unity is installed, but gdm says [Failed to load session "ubuntu"].
3)Without gnome-shell: Gnome shell in installed, but when I log to  gnome, I end up with a nautilus desktop, without gnome panels.Between the things that probably keep being broken in my old new ubuntu, was "libgl1-mesa-swx11" I think it kept my system from using opengl... removing it seems to have fixed all...

Don't know if lightdm is now fixed, I don't care.

---

