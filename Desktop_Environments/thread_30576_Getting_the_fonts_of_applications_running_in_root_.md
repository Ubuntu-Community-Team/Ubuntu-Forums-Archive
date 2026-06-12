---
title: "Getting the fonts of applications running in root to match..."
date: 2005-04-29
forum: Desktop Environments
---

### Post by ubersoft on 2005-04-29
So I've installed Kubuntu and I've got everything almost working the way I want it. I do have one problem, though...

All of the applications that run in root (Kynaptic comes immediately to mind, but also the KDE user manager and a few others) have font settings that are much, much larger than my local font settings. And unfortuantely there seems to be no way to change them!

In mepis or Xandros I'd just log in as root, fire up kcontrol, and change the font settings to match my user environment... but Kubuntu doesn't allow you to log into a root account (not a graphical one, anyway)... and I can't figure out a way to do the same thing with sudo.

So how can I fix this? Any thoughts?

---

### Post by TravisNewman on 2005-04-29
you can either do sudo kcontrol, which will give you kcontrol for the root settings, or run "sudo passwd root" and set a root password, which will enable you to login as root. I'd suggest the first.

---

### Post by ubersoft on 2005-04-29
Well... neither has worked for me.

I did sudo kcontrol, and I was able to access the font settings from there... but the only font sizes I seem to be able to affect are the fonts sizes ON kcontrol. Kynaptic fonts are still displaying at 12pt. type, when I've set the menu text to 8pt. type.

I actually had to use "sudo passwd root" in order to create a proper root password to install an inkscape cvs autopackage -- it wouldn't recognize my account password -- but even with an "active" root account, Kubuntu will not let me log in to a root session. When I try I get a message saying that I'm not allowed to do that.

All in all, it's very frustrating.

---

### Post by ubersoft on 2005-04-29
I wonder if the problem is that when you first log in to an account, KDE generates a bunch of files where it stores session information... and because I can't log in to the root account, those files haven't been generated yet.

---

### Post by dhanish on 2005-05-08
Solved this one by creating a custom theme with the current user then imported that theme by running "kdesu kcontrol".

Only thing was that each time I change theme settings I had to update that so instead I just made a link for /root/.kde to /home/user/.kde

No problems yet so far, not sure if this is the way it should be done it works.

---

