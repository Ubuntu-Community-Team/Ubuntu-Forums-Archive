---
title: "KDE 4.0.0 missing icons"
date: 2008-01-15
forum: Desktop Environments
---

### Post by catanzag on 2008-01-15
Hello to everybody,

after installing KDE 4.0.0 in kickoff I found no icons (only blank spaces) for most of new KDE 4 applications, and question mark icons for most of categories icons (apart from Education if I well remember, I'm not at my ubuntu box now). I got the same for the Add Widgets dialog where only few plasmoid have their own icon. Even changing icon themes gave no solution.

I found in the forums that some other users have the same problem, but I found neither if this is a known bug nor if there is now a workaround. What is your experience on this?

thanks and regards

catanzag

BTW, I uninstalled KDE4 and then installed again (with no errors/warning in console), but the problem remained; I've never tried betas or RCs, so I cannot say if it before worked.

---

### Post by GeneralZod on 2008-01-15
Someone in IRC mentioned that the latest Kubuntu updates fixed this.

---

### Post by catanzag on 2008-01-15
Thank you for the info!! I've just checked on [https://launchpad.net/~kubuntu-members-kde4/+archive](https://launchpad.net/~kubuntu-members-kde4/+archive) and in fact I've seen that a couple of packages (kdebase-kde4 and kdebase-workspace) were updated yesterday evening, when I'll have a few time on my ubuntu I'll make an update.

regards

catanzag

---

### Post by catanzag on 2008-01-18
After updating the available packages from ppa.launchpad.net, the situation is slightly improved, but it is not full fixed. I mean, apart SystemSettings, all other KDE 4 application finally show their icon in KickOff (and not blank space as before), but all categories icons are still with question mark.

Question mark icons are also in the icons of some widgets from extragear-plasma in the Add Widget dialog and in the categories in the screensaver dialog.

---

### Post by stikonas on 2008-01-20
Do you see language flags systemsettings->Regional & Language?

---

### Post by catanzag on 2008-01-29
Yes (sorry for my very late answer) I can see all the flags icons there, the only icons I don't see are in the menu.

---

### Post by alexrudd on 2008-02-15
Everything but Education is missing for me at the top level.

They've been missing since the initial release; I've been waiting for an update to fix but I guess it isn't coming.

---

### Post by jlacroix on 2008-02-15
If you're talking about how everything is a question mark, it probably won't ever be fixed because the problem is that KDE4 and KDE3 cannot coexist on the same Linux installation without one giving the other problems, at least as far as Ubuntu is concerned.

For example, I fixed the missing icons in KDE4 by setting each one to default manually. Then, when I logged into KDE3, my fixing KDE4's menu screwed up KDE3's menu and made some of its icons blank. Then, I fixed it in KDE3 and logged into KDE4 just to find KDE4's menu screwed up again.

I literally have to choose which desktop I want to have a messed up menu.

That's not the only problem I have. When I am logged into KDE3, and I run kmenuedit, it runs KDE4's version instead. Even when I access it from KDE3's taskbar!

I could go on, there are TONS of problems. I've come to the conclusion that you can't possibly have KDE3 and KDE4 on the same Linux installation without problems. If you do have both KDE3 and KDE4 installed and you aren't having problems, you ARE having problems you just don't notice them.

Even worse, if you have KDE4 installed by itself without KDE3, then you will more than likely have blank/question mark icons for everything because whatever KDE3 library they packaged KDE4 to depend on isn't there. That's completely absurd, why in the hell would they make the KDE4 packages depend on KDE3 libraries?! Not everyone wants both!!! (Perhaps depend is the wrong word, KDE4 in Ubuntu won't work correctly with the menus until kubuntu-desktop is installed).

The only solution for me is to find a way to make KDE4 not access any of KDE3's configuration files, I don't think you can do that yet.

Sorry to rant in this topic, but I've suffered with this menu problem to the point it caused me a reinstall. 

KDE4 is great, but the packages supplied for Ubuntu are horrible!

---

