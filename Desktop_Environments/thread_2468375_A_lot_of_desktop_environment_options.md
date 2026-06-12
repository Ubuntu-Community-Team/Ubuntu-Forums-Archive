---
title: "A lot of desktop environment options"
date: 2021-10-27
forum: Desktop Environments
---

### Post by akshajsingla on 2021-10-27
[https://drive.google.com/file/d/1-1kDry5x1qUqIQxKvtxKX7dG-l4o-qTH/view?usp=drivesdk](https://drive.google.com/file/d/1-1kDry5x1qUqIQxKvtxKX7dG-l4o-qTH/view?usp=drivesdk)


Here is the image I am getting while logging in . where I choose desktop environments.

What happens if I choose something 

- Gnome (any) - Oh no something went . A problem has occured which system cannot repair please logout and try again.

- Xubuntu - Unable to determine Fail safe session

- Ubuntu desktop - Same as gnome 

- Lxqt - working 

I want to run both gnome and Xubuntu and Lxqt desktop at same time , It is ubuntu 21.10

---

### Post by coffeecat on 2021-10-27
@akshajsingla, please upload your image to the forum using the paperclip icon in the advanced message editor. Your link gives an "access denied" message even to someone logged into a google account.

---

### Post by ActionParsnip on 2021-10-27
You can't run the desktops at the same time. You choose one at login time to be the active desktop environment and it will load with the setting for your user. You can run the applications from the different desktop environments without any issue
E.g LXTerminal can run in Gnome. You can run Gedit in LXQt

---

### Post by grahammechanical on 2021-10-27
A fresh install of 21.10 would only have two options. Ubuntu = Ubuntu on Wayland. Ubuntu on Xorg. You have all those options because you are using an installation that has been upgraded through several releases. When we do that things do get messy. It is possible that the code for those Gnome options is not in the 21.10 repositories.

It is also possible that as 21.10 is a recent release that the code for the Xubuntu and the Xfce session have not been upgraded by the developers to work in 21.10.

Last year I did an upgrade (18.04 to 20.04) and I was invited to authorize the removal of obsolete packages. I confirmed the removal and the Unity desktop got removed and also the code for those Gnome options. I ended up re-installing Ubuntu 20.04 to get an installation that was not messed up.

You have a working desktop environment. You could try re-installing the Xubuntu and Xfce desktops and that might fix those two for you. I do not know what to suggest about getting the Gnome desktop back whether on Xorg or Wayland. I am thinking that one of those Gnome options is Gnome classic.

Regards

---

### Post by Paddy Landau on 2021-10-31
As @ActionParsnip said, you can't run more than one at the same time. However, you can swap between them each time you log out and log in again.

But.

When you swap between different desktop environments for the same user, this can easily lead to conflicts that mess you up. If you have a powerful reason to use more than one desktop, use each one on a *different* user to prevent this sort of conflict.

Good luck!

---

### Post by guiverc on 2021-10-31
Sorry I don't really understand your question so I've not made a comment before.

I suspect your options are rather similar to what this box has though.

My box was a Ubuntu install; so I had GNOME options, but then I added
- `lubuntu-desktop`  (which was LXDE back then, is LXQt now; and of course `openbox` choices is included with a lubuntu install)
- `xubuntu-desktop` (ie. Xfce or Xubuntu choice
- `ubuntu-mate-desktop`  (ie. giving me MATE choices.. I've since removed this)

so my choices would be rather similar (*I'm not going to logout & confirm*); I have three just for Lubuntu (Lubuntu, LXQt & openbox - so you don't have all of Lubuntu I suspect), as I recall two for Xubuntu/Xfce, many for Ubuntu/GNOME & more..

If you have issues with GNOME - I'd suspect your issue relates to extensions; especially if you've upgraded your system (extensions are built to work with a specific GNOME & GTK version; they often work in a few similar versions, but if you *release-upgrade* thus change your version of GNOME; problems can be expected).

Xubuntu or Xfce can save sessions; if multiple sessions exist - you'll be asked which you want to use.

However I wonder if you're missing packages; as a fully installed Lubuntu system provides the three options I've already mentioned, ie.
- Lubuntu  (*all Lubuntu configs are utilized; I don't see this option for you*)
- LXQt (*a purer upstream config is used; few Lubuntu configs are implemented*)
- openbox  (*LXQt is WM agnostic so doesn't provide one; Lubuntu uses `openbox`; as it can be used without LXQt/LXDE; it's available to be used by itself*)

Your issue maybe also how you installed packages (ie. you didn't install everything required for some desktops), given what you provided in picture form doesn't look like all of Lubuntu was installed..  maybe the same applies to GNOME or Xubuntu/Xfce; or your partial-installs of desktops caused complications..  The multiple listings of "GNOME" would go along with this (and I don't mean "GNOME on Wayland", "GNOME on Xorg", "GNOME", "GNOME on openbox" etc.. but the 2x "GNOME" I'd not expect with correct package installations)


As already stated by others, I select which desktop/WM I want to use for the current session; only one will run.  I'm not limited to using those apps/toolkits/libs though; ie. currently it's Lubuntu (ie. LXQt with Lubuntu configs), where I'm using GTK2 apps too (hexchat), GTK3 apps (liferea, evolution etc), as well as native Qt5 apps (qterminal, featherpad etc) - but that's not using multiple DEs; my DE is LXQt, my WM is openbox etc.

---

### Post by TheFu on 2021-10-31
There are methods to run the different DEs concurrently.

As Paddy says, the easiest answer is to setup a different userid for each DE. This will keep the configuration files for each DE in a separate HOME directory and prevent conflicts between different DEs using the same config settings. The config conflicts mainly happen in Gnome software.  That's why you aren't seeing the same issue in the LXQt-based DE. It doesn't use Gnome stuff. Rather, it uses Qt stuff.

After you setup different userids, you can place them all into the same unix group and allow the group to share files in a read-write way.  That way, all the files owned by any of the 3-6 userids can be modified by the different users.  This is basic Unix group stuff.  There is a little more to getting it working, but if you search these forums for "working together", I've posted steps. [Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp) should have that stuff.

I haven't played much with 21.10 - too new for me and not an LTS - but if it supports the "change user" screen at login, then you should be able to login as each different user to have a different DE without logging out from the other users.  There are other methods too, but Gnome3+ doesn't work with those. LXQt and older Gnome2-based DEs should work fine.  Also, if you don't need the full desktop (that's a Windows-user thing), you can just open a terminal for each different userid and run the GUI programs inside those as needed.  This is standard Unix stuff going back ... perhaps 50 yrs?  I use it a few times each week.  One of my userids cannot run any snap packages because it uses NFS storage that is mounted outside what the snap programmers hard-coded into their system.  So, I setup a local account in the place they expect to be able to run a snap once a week - or about that often.  To access it, I open a terminal and **sudo -i -u thefu-local**, That gets me a terminal session as "thefu-local" where I can run any programs needed as the other userid.

---

### Post by hk42 on 2021-10-31
I think I'm the winner as I have 2 more options:
Kodi and Ubuntu studio. :-)
They all seem to work but I mainly use Ubuntu.
It's nice to be able to try other environments.
The idea of having different users is good as IIRC each keeps its last choice.

---

### Post by dirtydog01 on 2021-11-28
I'm a big fan of KDE.

---

### Post by Shibblet on 2021-11-29
> **dirtydog01 said:**
> I'm a big fan of KDE.

Booyah! (Geezus, how old am I?)

Agreed.  KDE has been my favorite for a long time.

In all actuality, one of KDE's options is if an application doesn't have KDE integration, it will use Gnome-Style Window management.  So, it's a win-win for me.

---

