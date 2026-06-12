---
title: "Unity is broken"
date: 2014-06-07
forum: Desktop Environments
---

### Post by Dave_Jury on 2014-06-07
I have 14.04 Trusty installed, and I have broken it somehow while trying to fix the issue of resume from suspend (this is a separate issue). Now, after logging in, instead of the unity task bar I get "Activities" at the top (is this Gnome desktop?). So, I can use this to open a terminal, and run "dconf reset -f /org/compiz/" and then "setsid unity".

Now I get unity back (yay!) but when I reboot it doesn't stay there (boo!). Also, under System Settings my "Appearance" icon is missing and probably a few others I haven't noticed).

I have done ctl-alt-f1 and in the terminal run "sudo apt-get install --reinstall unity" and "sudo apt-get install --reinstall ubuntu-desktop". Neither of these seem to help either.

Does anyone have any ideas, please, on how I can reset whatever could be broken so unity restarts. I do have a full backup, but it's a painful route to restore and then update with latest emails, documents etc changed since the backup.

---

### Post by grahammechanical on 2014-06-07
Did you install Gnome Flashback or Gnome Classic? One or the other will give us "activities" depending on the circumstances. Gnome Flashback gives us two additional login options - Gnome flashback (Compiz) and Gnome Flashback (Metacity).

It could be that Compiz is not loading and you are logging in to Flashback running on Metacity. I have Flashback installed on my Ubuntu development version just in case an update breaks Compiz. I can use Metacity to get to a working desktop. To reset Compiz

```
dcof reset -f /org/compiz/
```

If you are running on Metacity then you might want to remove and re-install Compiz Configuration Settings Manager and plugins extra (if installed) or even re-install Compiz. Another question: Did you disable the Unity plugin in CCSM? Doing that will cause something like this to happen.

Regards

---

### Post by Dave_Jury on 2014-06-07
Hi, thanks for your advice, which certainly steered me in the right direction. I have fixed it now, through sheer blind luck, and in spite of my tremendous ignorance. Your reference to Gnome certainly helped, and here's what I did in a terminal window (not tty):
"sudo apt-get remove gnome-shell"
"sudo apt-get remove compiz" (this removed ubuntu-desktop and unity as well)
"sudo apt-get install ubuntu-desktop (this installed compiz and unity as well)

That's it! Fixed! I still don't know why gnome-shell would be messing this up, but just removing and installing compiz, ubuntu-desktop and unity on their own without removing gnome-shell didn't work.

---

