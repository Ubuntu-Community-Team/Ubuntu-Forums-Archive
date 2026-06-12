---
title: "Every icon has vanished from Kubuntu"
date: 2006-07-30
forum: Desktop Environments
---

### Post by McSnuffy on 2006-07-30
Hello. I've done a few different searches of the forum and I have not found a thread relating to my problem, but forgive me if this is a repost. Today I was in the control center of Kubuntu, changing window decorators when I needed to open my home folder for something. On my taskbar, the button for the home folder was intact, but when I clicked it, the bouncing launch feedback icon was a blue square. I really got scared when Konqueror opened, however. Every navigation button was missing. No arrows, nothing. The icons for folders and files still existed, but everything else seems to be gone. The same is true for the programs in Kmenu. They have no icons. When I chose to edit an item however, its icon is still visible in the corner. The problem persisted after restarting X, and the icons show up just fine in GNOME. 

I am no expert, but I think this problem is being caused by some sort of permissions error with my icons. I don't know where the directory for icons is located, or if this is even the case, however. If somebody here has had this problem before, or thinks that they know what is going on, his or her help would be greatly appreciated.

**Quick update:** 'kdesu konqueror' runs the browser with every icon intact, further suggesting that some weird permissions crap is to blame.

---

### Post by NeoChaosX on 2006-07-30
Have you tried changing to a different icon set to see what happens?

---

### Post by ltmon on 2006-07-30
The normal iconsets are stored in /usr/share/icons and any custom sets you have installed are stored in ~/.kde/share/icons.

You could check that these directories are intact and have the correct permissions.

This snippet should reset the permissions of /usr/share/icons to the default permissions so that everyone can read them and execute (open) any directories:

```

sudo chown -R root.root /usr/share/icons
sudo chmod -R a+w /usr/share/icons
sudo find /usr/share/icons -type d -exec chmod a+x {} \; 

```

L.

---

### Post by Jucato on 2006-07-30
Try changing icon themes first, before you do something like changing permissions. Some GNOME-only icon themes that were installed by Synaptic or Adept are visible in System Settings, but are not really useable.

---

### Post by McSnuffy on 2006-07-30
Thanks for the response everybody, but my problem is not solved yet. :(

I tried using a different icon set. The 'Tango' theme created icons for some applications listed under Kmenu and also allowed navigation buttons to show up in Konqueror, but overall, it was ugly, incomplete, and cluttered. The GNOME icon set didn't even show up in Konqueror. I then followed ltmon's instructions and tried changing the icon permissions back to their defaults. This didn't solve anything either. Now I find myself sort of stuck. The fact that icons show up with 'kdesu konqueror' proves that none of them are missing, but the fact that the icons still won't show up for applications not run as root, even though the permissions are correct, suggests that my problem is not permissions-related. 

Does anybody have any other ideas? Thanks.

---

### Post by Jucato on 2006-07-30
Tango and GNOME icon themes are examples of the themes I mentioned, themes that are installed but work only in GNOME, not in KDE. Try changing to a KDE icon theme like the default Crystal SVG.

---

### Post by McSnuffy on 2006-07-30
Besides Crystal SVG, (which is the one that isn't working right now) are there any other KDE icon themes that are installed by default? I really don't feel like going over to kde-look.org and finding an entire icon set and then installing it.

---

### Post by ltmon on 2006-07-30
I think there is also HiColor, which is not very pretty at all.

You could create your own local version of CrystalSVG with:

```

cp -r /usr/share/icons/crystalsvg ~/.kde/share/icons/

```

Then use that theme.  It should have it's permissions set correctly for you to use.

Another good (and complete) icon theme available at kde-look is called CrystalClear.  I use this and it's very good.  Installing is simply a matter of dragging the archive containing the icons onto the correct dialog in the "System Settings -> Look and Feel -> Icons" page.

L.

---

### Post by Jucato on 2006-07-30
not installed by default, but installable from the repositories: nuvola, crystal, crystalclear, and nuovoext. 

Remember that when you install this from the repositories, they will be installed in the /usr/share/icons directory. Icons that you add yourself (through the "Install Icon Theme" of System Settings > Appearance > Icons) will be added in ~/.kde/share/icons directory and can only be seen/used by your user.

---

### Post by McSnuffy on 2006-07-31
Heh, I'm getting a bit sidetracked here... Just what file do I select to install an icon theme in the Appearance -> Icons section? A .tar.bz2 file containing the theme is not a valid format, a .theme file is not a valid format, and a .chache is not a valid format either.

Still, I would like to fix my current icon woe rather than simply installing a different theme...

---

### Post by Jucato on 2006-07-31
.tar.gz is the valid format accepted by the Icon theme module.

---

### Post by McSnuffy on 2006-07-31
Thank you.

I was able to install the Crystal Clear theme, which changed my folders and file icons, but failed to create any navigation buttons for Konqueror. There were still no application icons in Kmenu either.

---

### Post by Jucato on 2006-07-31
I'm thinking that this is a user-specific problem. One way to test it is to create a new "dummy" user and log into that. If all the icons are fine, then it's definitely something that affects only your user. If not, then it's a system wide problem, which I hope it isn't.

---

### Post by McSnuffy on 2006-07-31
I just created a 'guest' account. Every icon is where it should be. That's certainly good news, even though it confuses me.

---

### Post by Jucato on 2006-07-31
Hmm... I'm not sure if this would work, but it's worth a shot.

Try renaming the icons directory in ~/.kde/share into something else, like icons_backup. Log out, and log back in again.

---

### Post by McSnuffy on 2006-07-31
Ok. I'll try that now. I don't know if this means anything, but there wasn't an 'icons' directory in my /.kde/share directory until I made one in order for ltmon's instructions for copying CrystalSVG to work.

**EDIT:** Changed the name. Nothing is different.

---

### Post by Jucato on 2006-07-31
ok... try deleting that icons directory (~/.kde/share/icons).

Hoping it works... :(

---

### Post by McSnuffy on 2006-07-31
Deleting the 'icons' folder did not change anything. It didn't even create a new 'icons' folder. Then again, for my 'guest' account, there is no 'icons' folder in the /.kde/share directory and everything works fine. This is most perplexing.

---

### Post by Jucato on 2006-07-31
I bet it has something to do with one of the configuration files in the ~/.kde directory. Unless I could pinpoint that exact file/folder, the only solution I could think of is the most drastic one: rename ~/.kde into something else (like ~/.kde_temp). Unfortunately, this would reset everything to the default settings. If you've already customized so many things to your heart's content, this might not be an option.

I'll snooping around some more... :(

---

### Post by McSnuffy on 2006-07-31
I just need to clear some things up before I try this.

1.)Would renaming the directory to 'kde_temp' would create a new 'kde' directory automatically?
2.)Would renaming 'kde_temp' back to 'kde' restore my current settings?
3.)If it does reset everything to default, it would just be the color schemes, desktop layout, window decorations, etc that are reset to default. It wouldn't affect anything else, correct?

If that is the case, then resetting KDE to its defaults doesn't sound too bad. I would just have to change the desktop and edit the kicker a bit.

---

