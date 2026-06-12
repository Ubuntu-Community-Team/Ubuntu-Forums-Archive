---
title: "Auto Login Issue"
date: 2006-06-16
forum: Desktop Environments
---

### Post by jgcamp99 on 2006-06-16
Well, tonight I got home and booted Ubuntu 6.06 up and found 82.5 MB of updates. So I install them and it looks like Ubuntu went to a new kernel version and in so doing upgraded everything gnome. It was:

Ubuntu, kernel 2.6.15-23-k7

now it's showing as:

Ubuntu, kernel 2.6.15-25-k7

at bootup in Grub. Grub even shows the two kernel options in K7 and 386 flavors with both the plain kernel version as indicated above and another for recovery mode. 

Well, I was able to auto-login prior to the update, before without being prompted to provide the auto login users password. After these updates, it tries to auto login with the same user, but I get this small pop-up that requests the password. Anyone else get this from the update process ? Any ideas as to why it knows the user, but no longer remembers the password ? I've tried several times to disable auto login, reboot and then reset auto login, thinking it might clear the problem or figure not only both the user, but the password as well. Each time it goes back to the same little pop-up that requests the auto login user's password. I even tried creating a totally new user and setting that user as the auto login. Still the same results, Ubuntu knows which user I want auto login for, but prompts for the password in every auto login attempt.

---

### Post by macnerd on 2006-06-16
I ran into this tonight as well.  I built a new desktop, installed and ran updates.  I now have this same password box for auto login.

---

### Post by Benjamin_Lebsanft on 2006-06-16
[QUOTE=macnerd]I ran into this tonight as well.  I built a new desktop, installed and ran updates.  I now have this same password box for auto login.[/QUOTE]
same here

the corresponding bug is:
[https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49940/](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49940/)

---

### Post by jgcamp99 on 2006-06-16
Ben, from your bug report, I take it when you reverted back to the next oldest gdm, Ubuntu auto logins that user properly knowing both the user and it's password ?

If that's the case, I don't mind going back and getting that version, but will wonder if the update feature will forever detect that I have an update that needs to be done. This is probably something that will get fixed in no time at all, will be another update. But in the mean time, the auto login password prompt is annoying. If I uncheck auto login and go back to loging every user in with user id and password, wondering if it'll miss the update to fix it ?

---

### Post by jgcamp99 on 2006-06-16
Ben, I did what you did force the prior version and it works again, but that one update is out there indicated as undone, either way both the password prompt or update available is an annoying cloud over auto logins.

---

### Post by dcstar on 2006-06-16
[QUOTE=jgcamp99]Ben, I did what you did force the prior version and it works again, but that one update is out there indicated as undone, either way both the password prompt or update available is an annoying cloud over auto logins.[/QUOTE]
If you want to use a previous version of something and not be annoyed by Update prompts, use the "Lock Version" feature to mark the package as "Pinned" in Synaptic.

Be aware that you will have to manually "Unlock" the package if you want any future update notifications for it.

---

### Post by jgcamp99 on 2006-06-17
"If you want to use a previous version of something and not be annoyed by Update prompts, use the "Lock Version" feature to mark the package as "Pinned" in Synaptic.

Be aware that you will have to manually "Unlock" the package if you want any future update notifications for it."

That always has distrubed me, even with windows update, to have to hide updates for hardware driver updates that didn't work or were worse than the original driver. I wa shoping that package of gdm would be fixed in short order and become available as a minor update to gnome.

---

### Post by deathbyswiftwind on 2006-06-17
i to have this problem but since i only restart like once evey 4 days it dont matter all too much

---

### Post by mula on 2006-06-17
I have the same annoying issue. I just hope it's a bug, not a feature so they would fix it as soon as possible.

---

### Post by rumli on 2006-06-17
I had the same problem.  There were more updates subsequently which seemed to fix the problem.  Try running the Update Manager (in the System / Administration menu) and checking for new updates.

---

### Post by RRS on 2006-06-17
Bug has ben fixed. I ran "apt-get update" last night and auto-login now back to normal.

---

