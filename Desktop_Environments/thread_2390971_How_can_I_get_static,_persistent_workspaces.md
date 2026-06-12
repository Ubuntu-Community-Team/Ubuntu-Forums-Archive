---
title: "How can I get static, persistent workspaces?"
date: 2018-05-04
forum: Desktop Environments
---

### Post by DocSavage1940 on 2018-05-04
What I'm really wishing for was way back in KDE, several years ago when I had several virtual desktops that were permanently populated with apps for my particular purpose. Back then, I could even have a different background for each. Pretty slick, productivity-wise. More recently on Kubuntu, KDE I had several activities (no more virtual desktops) that persisted and had a title. Every time Linux started up, there they were. I could select the particular 'activity' that was configured for the task at hand.
Now I've upgraded to a real Ubuntu, version 18.04.
I can put an app on an 'activity' and a different app on a different 'activity.' and I can go the switcher and select where I want to be. But I can't title them for easier navigation. More importantly, when Ubuntu reboots, they are gone. I have to start over with the organization.
Is there a way, with this snazzy new Ubuntu for me to create 3 or 4 ...'spaces.' or virtual desktops or activities or workspaces or ...I don't care what they are called. So that when I boot Ubuntu, there they are, waiting to be selected with titles like 'forums' or 'site updates' or 'comms,' or some task I repeat, already populated with the app I want for that task. Chromium or Firefox or Slack or...whatever?
As configurable as Linux is supposed to be, there must be some way I can make this OS work for me instead of against me.

---

### Post by deadflowr on 2018-05-04
You can set static workspaces using Gnome Tweaks.
Installable through the Ubuntu Software center.

You can install an extension called auto move windows from the gnome extensions website which will allow to set specific workspaces for particular apps to open in.
Here's the auto move windows extension page:
[https://extensions.gnome.org/extension/16/auto-move-windows/]("https://extensions.gnome.org/extension/16/auto-move-windows/")
(you also need to make sure you the chrome-gnome--shell package installed.
This allows you to add extensions from the website)

You can install both chrome-gnome-shell and gnome-tweaks via command line with:
```
sudo apt install gnome-tweaks chrome-gnome-shell
```
 I post the command as Ubuntu Software is bad at listing non-desktop apps, so I'm not sure if the chrome-gnome-shell package would otherwise be listed.

There are also a variety of pre-ready-made extensions available in Ubuntu-Software center you may take a gander at.
(auto move windows may or may not be listed in there already)


In terms of apps opening ready to go, I think you'll need to set them up to start in the Start Applications program.
I do not know if gnome's saved sessions works, as it has not for some time and I haven't tried to see if it does.


Hope it leads you in whatever direction you want to go.

---

### Post by DocSavage1940 on 2018-05-04
Thanks! now you gave me work to do, I'll get back to you...

---

### Post by DocSavage1940 on 2018-05-04
Thanks for the pointing me in the right direction.
I've done all you suggested. It's not where I wish to be, but it's a great improvement. 
I'll work with this configuration for a few days to get used to it.
Thanks again

---

