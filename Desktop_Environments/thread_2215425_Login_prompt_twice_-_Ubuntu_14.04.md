---
title: "Login prompt twice - Ubuntu 14.04"
date: 2014-04-06
forum: Desktop Environments
---

### Post by stormyk88 on 2014-04-06
So, I upgraded to 14.04 a few days ago, and am liking it so far. Only two real issues as of now. Please move to appropriate area if required.

1. Login Prompt - 
This just happened a day or so ago after having upgraded for a day or two. After going idle, I get the normal lock screen, and enter credentials to unlock. More often than not, after a few seconds, it reverts back to my lock screen again and I have to enter my password a second time. It only does this twice, never more. Any ideas for a resolution besides 'no authentication' ?

2. Theme issue - 
I found a theme on gnome-look that I like, and installed it. Can't remember what I was doing at the time, but I changed a color setting in Firefox (part of same problem or another issue by itself, not sure which). Basically, what I get is text input boxes for chat in a game I play (Kingdoms of Camelot if you must know) have a dark grey background, with white or light grey text, which is fine. I was going for a darker theme. But on most other web forms (only using FF for a browser) the text fields are white and text is light grey, making it difficult to read. I am sure this is only a matter of resetting FF, but how do I do that, and once that is done, is there anything I need to look for in a GTK theme?

Thanks for the help, as always.

Running, Ubuntu 14.04 / Gnome Desktop
uname -r
3.13.0-23-generic

Have also had several upgrades since upgrading, but everything else has been working flawlessly, including wireless, sound, video, etc.

---

### Post by grahammechanical on 2014-04-06
Hi

1) I do not get this problem on my Trusty Tahr. It have just tested for it. But I am running Ubuntu + Unity. It could be a bug in which case you can report it. It might be only 10 or 11 days to release day for Ubuntu 14.04 but update every day. Things often get fixed in time by an update. To a certain extent the 14.04 code is still a moving target for the developers of alternative desktops. It might be better to wait until the developers of these desktops have had a chance to upgrade their code to comply with the 14.04 code.

2) Is the theme GTK2 of GTK 3? It has to be GTK 3 since Gnome 3 and Gnome 3 Shell were released. I think the Firefox themes are a different matter from System themes.

Regards.

---

### Post by michal-mzl-zielinski on 2014-04-07
Ad 1. This is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/1292451").

---

### Post by stormyk88 on 2014-04-15
OK thanks all. Login issue has been resolved, and switched to another theme. All is good now.

---

### Post by armin-telegdi on 2014-04-16
I have this login prompt issue on 13.10 but with other conditions. It appears sometimes after wake from sleep.

---

### Post by wileycoleman on 2014-07-28
I had the problem with the double login as well. I am using cinnamon instead of unity.  Found the solution  here.  [http://askubuntu.com/questions/356992/how-do-i-disable-the-cinnamon-2-lock-screen](http://askubuntu.com/questions/356992/how-do-i-disable-the-cinnamon-2-lock-screen)
What worked was to do this in the command line:

gsettings set org.cinnamon.desktop.lockdown disable-lock-screen true

---

### Post by emagar on 2014-08-08
> **wileycoleman said:**
> gsettings set org.cinnamon.desktop.lockdown disable-lock-screen true

Any hint about what the equivalent for unity should look like?

---

