---
title: "KDE File Sharing"
date: 2005-10-30
forum: Desktop Environments
---

### Post by SadaraX on 2005-10-30
I am trying to get KDE file sharing to enable. When I go to kcontrol as a normal user, then go to 'Internet & Network -> File Sharing', and click the "Administrator Mode" button, it prompts me for my password. 

When I give it my password, it just goes back to the default start screen for kcontrol, with a brief summary of my system information (kernel, KDE version, etc). When I give the admin mode button the root password, it does the same thing.

How can I enable file sharing within KDE?

---

### Post by peanut butter on 2005-10-30
You know it wants _YOUR_ password not root's if you have root enabled.

---

### Post by SadaraX on 2005-10-30
[QUOTE=peanut butter]You know it wants _YOUR_ password not root's if you have root enabled.[/QUOTE]

I know that it wants my password. But since my password did no work, I decided to try the root password too, but that also did not work.

---

### Post by ltmon on 2005-10-30
Kcontrol has always been a bit screwy for admin mode in Kubuntu.

Best way to solve it for now is to launch kcontrol from the command line with:

> sudo kcontrol

L.

---

### Post by GoldBuggie on 2005-10-30
Since the admin button in the control settings aren't perfect I prefer right-clicking on a folder I want to share. Go to the sharing tab and do everything from there. Workes perfectly I think. You can actually setup other directories then the one you right-clicked on by doing this as well. Ayway...its an option..you choose your own preference.

---

### Post by lips on 2005-11-02
This is a reported bug:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8681](https://bugzilla.ubuntu.com/show_bug.cgi?id=8681)

Pretty serious IMHO.  Why it's not fixed I don't know.

---

