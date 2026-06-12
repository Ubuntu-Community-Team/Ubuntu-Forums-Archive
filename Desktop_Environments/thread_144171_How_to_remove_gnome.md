---
title: "How to remove gnome?"
date: 2006-03-13
forum: Desktop Environments
---

### Post by Zedzero on 2006-03-13
Hello. Gnome is very heavy and slow on my low-end notebook, and i'm thinking about installing fluxbox or xfce. I need to remove gnome, because i have very limited diskspace. Also i don't need any of the gnome applications.

- Which packages should i remove to completely uninstall gnome?
- Are there any applications which i shouldn't remove?
- Even if i remove gnome, is there a way to run gnome applications in the future if i want to?
- Are those applications which i used to run in Gnome (like synaptic) dependent to gnome?

Sorry if i asked silly questions. I'm total newbie to linux.

Thank you.

---

### Post by Adrian on 2006-03-13
Check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=96046](http://www.ubuntuforums.org/showthread.php?t=96046)

You will be able to run Gnome applications, like Synaptic, anyway.

---

### Post by Zelut on 2006-03-13
Well to install Xfce (which is super light--I love it) you could install the 'xubuntu-desktop' package.  After that is installed you can change your 'session' at login to Xfce and then you never hit gnome anymore.  You can also try to install 'xdm' & remove 'gdm' (xfce login manager vs gnome).

I'm not sure on the dependencies of apps like Synaptic and gnome.  I know there are a few things that I like to keep around from gnome when using Xfce.  If you can afford the disk space you can easily keep both on the machine.

---

### Post by Adrian on 2006-03-13
If any GNOME applications you want is removed by following aysiu's howto, you should be able to reinstall them (and get the stuff they depend on automatically at the same time).

---

### Post by bluevoodoo1 on 2006-03-13
[QUOTE=Adrian]If any GNOME applications you want is removed by following aysiu's howto, you should be able to reinstall them (and get the stuff they depend on automatically at the same time).[/QUOTE]

Or... just take the apps you want to keep out of the list of things to be uninstalled. 

I followed aysui's guide on removing kubuntu-desktop. I removed everything except amarok, k3b, ksnapshot and a few other apps from the long list. They work fine on gnome and I haven't had any problems with them.

---

