---
title: "Can't edit user accounts in Xubuntu 12.04."
date: 2013-07-08
forum: Desktop Environments
---

### Post by BR8 on 2013-07-08
I'm not sure if this is the right forum, but it seems to be related to DEs.

Background: Windows XP broke, I installed Xubuntu from a previously made LiveCD, all was well after that was accomplished.

I installed Unity, KDE, LXDE, Cinnamon, GNOME, and Metacity so my mom could try them to see which she preferred, but she didn't and I figured "XFCE's alright, so I don't need the others."

I uninstalled the other DEs, and now I seem to have no way of editing user and group accounts. After uninstalling some of them, I had to reinstall the Screensaver Settings, but I don't know how to retrieve the other Settings, and I don't know if there are any others that I'm missing. I tried reinstalling xubuntu-desktop with Synaptic, but it didn't seem to help.
[IMG]http://fc03.deviantart.net/fs70/f/2013/189/7/e/remaining_settings_by_br8n03epsilon-d6cmg9y.png[/IMG]

These are the settings I still have, I'd like to know if any are missing.
Any help is appreciated. Also, sorry about the blue squares, I used Pinta and something must've glitched.

---

### Post by Toz on 2013-07-09
Just booted up the 12.04.2 LiveCD and it looks like you've got all the default ones there.

On the base install, the gui user/group management tool is located in the System menu. If its missing, install the **gnome-system-tools** package.

---

### Post by BBQdave on 2013-07-09
> **BR8 said:**
> I uninstalled the other DEs, and now I seem to have no way of editing user and group accounts.

Uninstalling DE's tends to rip out programs needed by the remaining DE. Not to be a bummer, but the most straight forward way to have a full function Xubuntu DE - fresh install.

Save time and frustration, back up your data and do a fresh install of Xubuntu :)

---

### Post by BR8 on 2013-07-09
Thanks for the suggestions. I installed LXDE, then un- and reinstalled xfce4-settings, xfce4-seesion, andd xubuntu-desktop. I can now edit Users and Groups and nothing else seems to be amiss.

---

