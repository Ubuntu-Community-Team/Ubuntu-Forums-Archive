---
title: "When to reboot or restart after installing package updates"
date: 2005-03-10
forum: Desktop Environments
---

### Post by superhac007 on 2005-03-10
This has been a question I have had for a very long time.  When you update a package do you need to restart anything or reboot?  Obviously you need to reboot when you install a new kernel.  But what about the other packages?  I've also noticed that service based packages will automatically restart themselves during the package installation.  Which tells me those are running at the latest revision, right?  What about shared libraries?  Will a program that uses these shared libraries automatically use the newest or do you have to restart the app?  

Is there any general rule for knowing when to restart, reboot or what needs to be done after a package has been upgraded to insure that latest update is being used? 

Thanks!

---

### Post by bored2k on 2005-03-10
Not really, it depends on the package tho.

If you want you can ctrl alt backspace to reset X and then re-login. You would only want to restart your computer mostly on system changes and such.

---

### Post by paul cooke on 2005-03-10
generally, for everything except a Kernel update, I log out, do a "ctrl+alt+backspace" to restart the X server and then log back in again... it saves so much grief when some apps behave very weirdly when stuff like Gnome or KDE has had some updates.

Most of the time, I'm the only one logged in anyway, so it doesn't inconvenience me very much, but if your running server stuff and others rely on the machine being there, then it can make sense to warn them your restarting/updating stuff.

I'm sure some more experienced "admins" will jump in here with advice on things in this situation, but generally, when using synaptic or apt-get to do updates, the update itself will restart the service affected.

Doing your updates in the wee small hours using a Cron job will make things much easier for those cases. But if you are seriously adminning a system, then do the updates first on a test machine to make sure things go smoothly... sometimes, you may find that you are  prompted for input during an update because a script or config file is being changed.

---

### Post by bored2k on 2005-03-10
[QUOTE=paul cooke]generally, for everything except a Kernel update, I log out, do a "ctrl+alt+backspace" to restart the X server and then log back in again... it saves so much grief when some apps behave very weirdly when stuff like Gnome or KDE has had some updates.

Most of the time, I'm the only one logged in anyway, so it doesn't inconvenience me very much, but if your running server stuff and others rely on the machine being there, then it can make sense to warn them your restarting/updating stuff.

I'm sure some more experienced "admins" will jump in here with advice on things in this situation, but generally, when using synaptic or apt-get to do updates, the update itself will restart the service affected.

Doing your updates in the wee small hours using a Cron job will make things much easier for those cases. But if you are seriously adminning a system, then do the updates first on a test machine to make sure things go smoothly... sometimes, you may find that you are  prompted for input during an update because a script or config file is being changed.[/QUOTE]
 I wish I had a test machine to test everything before messing up my box as I tend to do periodically... :\

---

### Post by paul cooke on 2005-03-10
that's why I hang on to other people's cast-offs... an old 300 MHz box may be far too gone for them as they've gone up to XP or whatever, but hogging it out to at least 256MB ram (which is very cheap for old PC100 based boxes) brings it up to spec for running Ubuntu very nicely... I use my big box to handle the major packages like OOo by running them using ssh over X or VNC. With the magic of Samba, you can run OOo remotely, yet still be editing files on your local machine.

---

