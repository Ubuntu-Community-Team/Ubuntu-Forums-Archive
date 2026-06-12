---
title: "Switching from LXDE to Gnome in Lubuntu - Requesting Files"
date: 2012-06-01
forum: Desktop Environments
---

### Post by dodle on 2012-06-01
Before I do a fresh install, I was wondering if anybody who is using Gnome on Ubuntu 12.04 would mind uploading an archive of the files located in /usr/share/gnome/autostart and, in another directory or archive, put the files from /usr/share/gdm/autostart/LoginWindow. I am trying to switch from LXDE and LightDM to Gnome and GDM on a Lubuntu install. Unfortunately, even after installing Gnome, these startup/launcher files do not exist and I can't seem to get them right. If this doesn't work, I will downoad a 12.04 iso and do a fresh install. Does the 12.04 Live CD give you the option to install Gnome in place of Unity?


**----- EDIT -----**

BTW, does 12.04 use GDM or LightDM by default?


**----- EDIT -----**

Oh, I just found the package ubuntu-desktop. I think that is what I was supposed to install. I will let you know if it works.


**----- EDIT -----**

After installing ubuntu-desktop I still needed to add gnome-panel to the startup applications list. Now I can login to Gnome but there are still some issues. gnome-panel doesn't seem to take on the system theme and right-click does not work on it.


**----- EDIT -----**

gnome-panel *is* taking on the system theme, I changed it to Ambiance and now it looks normal. But I still can't use right-click.


**----- SOLVED (right-click) -----**

Found the answer [here]("http://ubuntuforums.org/showthread.php?t=1852764"). I guess with the new gnome-panel you have to hold down [color=blue]Alt[/color] while right-clicking. This is my first time using Gnome Shell.

---

### Post by hictio on 2012-06-02
> **dodle said:**
> 
~snip~
Does the 12.04 Live CD give you the option to install Gnome in place of Unity?
~snip~


To the best of my knowledge, it doesn't.
Take a look at this project: [Ubuntu GNOME Shell Remix](http://ubuntu-gs-remix.sourceforge.net/p/home/)

It is basically a Precise Pangolin installed (live CD) that leaves aside Unity and installs Gnome 3 as the default DE, also installs the Classic Gnome.
I've been testing it for little over a week, and I'm really considering wiping my boxes and re-install using that one.

---

### Post by dodle on 2012-06-02
Thanks, I did end up installing the GNOME Shell Remix. But, I was having some similar issues with logging in. It turned out that I needed to use Classing GNOME in the login manager, most likely do to the old hardware I am using. Also, right-clicking on the desktop isn't working and there are a few packages that I would expect to be in a GNOME environment that don't come pre-installed such as gdebi and synaptic. So, at the moment I am installing the package gnome-desktop-environment which installs these packages and more and hopefully fixes the right-click issue.

**----- 1,000 BEANS!!! -----**

---

