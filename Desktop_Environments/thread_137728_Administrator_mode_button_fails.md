---
title: "Administrator mode button fails?"
date: 2006-02-28
forum: Desktop Environments
---

### Post by meburke on 2006-02-28
I had a switch problem when I installed kubuntu on my laptop, and I couldn't configure the network settings. Now, when I go to the system settings and try to configure the network settings, the screen tells me I have to use the administrator mode button to make changes. What happens after I enter the root password in the dialog box is I get a big red-bordered square with nothing in it and the dang thing goes back to the screen that tells me I need to click the administrator mode button.... I feel like Sysiphus. Do I have to re-install kubuntu from scratch? (ifup doesn't work in the console, and in the screen, both eth0 and ath0 are greyed-out.)

---

### Post by gingermark on 2006-02-28
Try hitting Alt+F2 and running kcontrol. If you still have the problem, do Alt+F2 and run kdesu kcontrol. Once you've entered your password, you'll be running kcontrol with root priviledges.

I think you can do kdesu systemsettings if you prefer Kubuntu's System Settings layout to KControl.

These are of course workarounds, but I think the problem is a bug, although I thought it had been solved. I'm running KDE 3.5.1 and certainly don't have these problems.

But yes, the kdesu command will open whatever application you want with root priviledges. Hopefully that will allow you do get what you need to do done.

---

### Post by Jucato on 2006-02-28
This is a bug I think in KDE 3.4.x.
Another thing is that I think KDE automatically enables network devices only if it is connected to a network (not the internet). meaning, (I'm not entirely sure about wifi though), it doesn't need to be enabled for it to connect to the internet. My eth0 is disabled but here I am typing these... (I find this really, really strange. :D)

---

