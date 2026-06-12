---
title: "I cannot log in to my account on Ubuntu desktop"
date: 2019-01-28
forum: Desktop Environments
---

### Post by siavosh-kasravi on 2019-01-28
[COLOR=#242729][FONT=Arial] see the log-in screen but when I select one and enter the password it fails to log me in. It easily enters into guest account by the way.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I suspected there is some graphical problem and checked Xorg log. There it couldn't access fb0 for permission problems.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I should note the problem started happening when I updated Ubuntu from 14 to 16.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I also looked at kernel log and noticed some problems there. So I started a new thread [here]("https://askubuntu.com/questions/1110848/vmwgfx-error-in-kernel-log-on-ubuntu-16-04") which didn't get any response.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So I uninstalled and re-installed lightdm and Xorg and Ubuntu-desktop with no success.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any idea on how to investigate the matter?[/FONT][/COLOR]

---

### Post by Autodave on 2019-01-28
I rarely see an update from one version to the next work well: it just seems that there are always weird problems.  Can you possibly do a clean install?  18.04 is out now, so you may want to think about doing that.  If you can get 16.04 or 18.04 downloaded and burnt as an .iso to either a DVD disk od a thum drive, you could at least boot with that and then any files that you need to keep copied to an external source.

---

### Post by siavosh-kasravi on 2019-01-28
OK, I should note something. The problem didn't exactly start after update. It began a little while after. First I could log into a new account I created but not the old one then suddenly couldn't log into guest.
I don't mind playing with kernel modules or drivers. I just need some advice on where to start.

---

