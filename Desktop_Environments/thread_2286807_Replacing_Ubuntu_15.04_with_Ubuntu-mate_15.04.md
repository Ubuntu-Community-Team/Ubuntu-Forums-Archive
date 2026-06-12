---
title: "Replacing Ubuntu 15.04 with Ubuntu-mate 15.04?"
date: 2015-07-14
forum: Desktop Environments
---

### Post by Ron_Erhardt on 2015-07-14
New here on the forum, and just getting back into the Linux world (started with Red Hat long ago). 

I recently installed Ubuntu 15.04 alongside Win 7 on my laptop, and fairly quickly decided that I do not like the Gnome desktop. I attempted an install of KDE Plasma; but never did get things to work and went through the uninstall process (mostly apt-get commands). One interesting 'artifact' after that is that I still get the 'kubuntu' icon when booting (not sure what causes that).

Then I followed the instructions at [http://sourcedigit.com/15861-install-desktop-environments-in-ubuntu-mate-gnome-kde-cinnamon-budgie/](http://sourcedigit.com/15861-install-desktop-environments-in-ubuntu-mate-gnome-kde-cinnamon-budgie/), and attempted to install Ubuntu-mate. Well...

- I *still *get the 'kubuntu' icon when booting
- After login I get 'Ubuntu MATE' logo on the screen; but...
- I still have the same Gnome desktop (and no apparent way to switch)

So...

I've downloaded the Ubuntu-MATE 15.04 ISO and written it to a DVD, just in case; but I'm reluctant to do anything with it because I've installed several programs and done some work with the existing Ubuntu 15.04 install, and don't want to have to redo all of that. 

Any solutions that can get me into MATE without a lot of rework?

---

### Post by v3.xx on 2015-07-14
As you found out, mixing kde and ubuntu can make a mess.  You should also have several kde packages showing up in your menu.

If you have successfully installed mate to this, you should see it at the login screen by clicking on the icon.
[ATTACH=CONFIG]263203[/ATTACH]

IMO, your better off doing a fresh install and avoid trouble down the road.

---

### Post by sammiev on 2015-07-14
Have you tried Ubuntu-mate from a USB/DVD first to see if it's what you want?

So far Ubuntu-mate has been great here.

---

### Post by Ron_Erhardt on 2015-07-14
> **v3.xx said:**
> As you found out, mixing kde and ubuntu can make a mess.  You should also have several kde packages showing up in your menu.

If you have successfully installed mate to this, you should see it at the login screen by clicking on the icon.
[ATTACH=CONFIG]263203[/ATTACH]

IMO, your better off doing a fresh install and avoid trouble down the road.

Thanks. That is what I was missing! I found mentions of 'clicking' on something at the login; but nowhere did it point me to that icon. I'm in 'mate' now.

I noticed the extra KDE packages, and thought I uninstalled/removed all of them. If the only remnant is the logo during boot, I'll live with it.

Thanks again. If I run into any unexplained phenomena over the next few days, I'll back things up and redo the Mate install from the ISO.

---

### Post by Ron_Erhardt on 2015-07-14
> **sammiev said:**
> Have you tried Ubuntu-mate from a USB/DVD first to see if it's what you want?

So far Ubuntu-mate has been great here.

Quick answer is yes, I did poke around on the 'live' DVD first. I like it a LOT better than Gnome. ;)

---

### Post by v3.xx on 2015-07-14
Sounds good

Don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

---

### Post by SantaFe on 2015-07-15
You might try this to switch back to lightDM, which Mate uses: [http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)



Whoops, I  just noticed it's the KDE Icon that's stuck.  I thought it was the KDE login manager.  Sorry.

---

### Post by Ron_Erhardt on 2015-07-18
Well...

As was suggested, I still have unresolved 'issues' with the system as it sits, and I'm ready to do a fresh install from the Ubuntu-MATE ISO; but I'd really like not to lose everything I've put into this one. I've already backed up some of the application-related stuff, and I'm pretty sure I understand how to put them back. From a web standpoint, I have Firefox, Chromium and Thunderbird e-mail installed, and I would very much like not to have to reset all of the accounts/cookies/settings etc. for them. 

So...

1) Is there a quick and painless way to save those things that I can reinstall once the new system is up?
and
2) When I boot from the Ubuntu-MATE 'live' DVD, will I have the option to install Ubuntu-MATE on top of the existing Ubuntu 15.04 system? If not, will the installer give me the option to delete the partition for the 'old' (current) system and create a new one for the new install?

Thanks in advance!

- Ron E.

---

### Post by v3.xx on 2015-07-18
Saving FF settings is easy.  Just copy the hidden Home folder ".mozilla" to the new install.  Chome should also have such a folder.

#1
There are a lot of differences between Unity and Mate.  Trying to exchange configuration files for installed applications will at best be questionable.  I think better to just reconfigure your new install.

#2
Everyone has there pet way.  I first use a partition manager to delete the current install, then use the "other" option when installing.  It will then have the option to install to the largest free space.

---

