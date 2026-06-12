---
title: "Kubuntu has no icons!!!!"
date: 2007-05-19
forum: Desktop Environments
---

### Post by Ryupower on 2007-05-19
HEY, 
OK, earlier I formatted and reinstalled ubuntu, this time Feisty. I then decided to install the kubuntu desktop, so I did. Problem: ICONS ARE MISSING IN IT. I reinstalled it a couple of times, bringing back the same results. There is no default icon theme! I had to try another one and the kubuntu 'start' menu button was still missing.

Anyways, then I tried formatting the partition again, this time installing kubuntu first ( working icons ), ubuntu second. and now I have the SAME problem!
Please, someone help! thx.


using: ubuntu CE, kubuntu, feisty, laptop.

---

### Post by Hairy_Palms on 2007-05-20
hmm all i can think of is hav you checked the md5 sum of the disc recently, also try checking the contennts of the /usr/share/icons directory,to see if the icons are actually there.

---

### Post by Ryupower on 2007-05-21
I checked it. They're there, and it won't install new ones! :(

The ISO was right, it also did this when I installed kubuntu-desktop from synaptic.

---

### Post by shane2peru on 2007-06-09
> **Ryupower said:**
> I checked it. They're there, and it won't install new ones! :(

The ISO was right, it also did this when I installed kubuntu-desktop from synaptic.

I have the same problem.  I wanted to take another look at kubuntu, and did a search in synaptic and installed kubuntu-desktop and it had a loooot of dependencies.  It installed I rebooted and booted into KDE, and no icons no anywhere!  No start button.  I went to system settings, and no icons even in the window that opens up.  I went back to Gnome, opened synaptic and installed kde-base (I think)  and looked for a few more things that may have been missing, and Nothing!  HELP!!!  I really would like to give KDE another look and try, but I would like to have icons to do it.  I know this has to be a simple problem like maybe permissions, perhaps a missing package or something?  I don't know.  

Shane

---

### Post by bunker on 2007-06-09
Make sure there is a symlink called default.kde in /usr/share/icons pointing to the root default icon set.

```
drwxr-xr-x  8 root root 4096 2007-04-22 02:05 Crystal
drwxr-xr-x  8 root root 4096 2007-04-22 02:05 crystalclear
drwxr-xr-x  9 root root 4096 2007-05-31 07:37 crystalsvg
drwxr-xr-x  2 root root 4096 2007-04-20 23:55 default
lrwxrwxrwx  1 root root   10 2007-04-20 23:50 default.kde -> crystalsvg
lrwxrwxrwx  1 root root   33 2007-04-21 23:05 emacs-snapshot -> ../emacs/22.0.91/etc/images/icons
...
```

If no icons are there at all, I guess you could try installing some from [www.kde-look.org](www.kde-look.org).

I don't know where the per-user icon settings are stored, but you certainly should be able to change it through kcontrol.

---

### Post by shane2peru on 2007-06-09
> **bunker said:**
> Make sure there is a symlink called default.kde in /usr/share/icons pointing to the root default icon set.

```
drwxr-xr-x  8 root root 4096 2007-04-22 02:05 Crystal
drwxr-xr-x  8 root root 4096 2007-04-22 02:05 crystalclear
drwxr-xr-x  9 root root 4096 2007-05-31 07:37 crystalsvg
drwxr-xr-x  2 root root 4096 2007-04-20 23:55 default
lrwxrwxrwx  1 root root   10 2007-04-20 23:50 default.kde -> crystalsvg
lrwxrwxrwx  1 root root   33 2007-04-21 23:05 emacs-snapshot -> ../emacs/22.0.91/etc/images/icons
...
```

If no icons are there at all, I guess you could try installing some from [www.kde-look.org](www.kde-look.org).

I don't know where the per-user icon settings are stored, but you certainly should be able to change it through kcontrol.

Ok, thanks!!!   I do have that symlink, however I guess I didn't have icons selected.  I ran kcontrol and selected an icon set, and poof, I now have most of my icons.  I was going to look at the link for a complete icon set but decided to check aptitude first and see what they have.  Apparently this was left off as a dependency, since it works without it I guess it isn't considered a dependency, however for me it is! :)  I searched for the icons and then installed them this way: ```
sudo aptitude install kde-icons-crystal kde-icons-crystalclear kde-icons-gorilla kde-icons-korilla kde-icons-mono kde-iconsnoia kdeartwork-emoticons

```

Hope that helps someone,  When they get installed I will go through kcontrol (alt-f2) then kcontrol and select a new complete icon set for kde.  Thanks for the help, you pointed me in the right direction.  :D

Shane

**EDIT:**  Ok, I still have an uncomplete set of icons.  If someone knows the correct package to install and select that would be great!  At least I have some icons now.

---

### Post by shane2peru on 2007-06-16
Ok, I think this is really a bug.  I have completely purged my old installation of kubuntu-desktop and then removed the .kde and .kderc folders from my home folder, and re-installed kubuntu-desktop.  
I installed it as follows:```
sudo aptitude install kubuntu-desktop
```
It even ran me through the setup for KDE when it started up.  First time logging into KDE NO, ABSOLUTELY NO ICONS!!!  I installed a 'Breathless' icon theme from kde-look.org and attached is the screen shot after logging out and back in.  It doesn't matter what I do, I CAN NOT GET A COMPLETE SET OF ICONS IN KDE INSTALLED OVER GNOME!!!  You will notice there are no icons inside of amarok or kopete as well as one missing icon on the panel!  Arrrgh!!!
[IMG]http://www.rices4peru.com/Gifs/snapshot1.png[/IMG]

If anyone has any help for this, I would appreciate the help!

Shane

---

### Post by Ryupower on 2007-09-17
ugh, so the problem isn't solved? :(

---

