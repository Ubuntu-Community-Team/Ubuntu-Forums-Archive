---
title: "Upcoming Kubuntu install"
date: 2005-12-14
forum: General Help
---

### Post by canadianwriterman on 2005-12-14
This weekend, I plan to do a fresh install of Kubuntu from my install CD. I understand that updating is different from Ubuntu, i.e., there are no automatic updates like Ubuntu has.

What do you recommend after installation:

Should I do a **kdesu apt-get update **then **kdesu apt-get upgrade **or should I just go to the **Adept** graphical installer and click on **Fetch Updates** and then Full **Upgrade**? Do I need to enable all the repositories first (and is that done in **Adept**)?

Thanks and keep your fingers crossed for me!

---

### Post by artnay on 2005-12-14
Add Kubuntu.org's 3.5 repo and key, details [here]("http://kubuntu.org/announcements/kde-35.php"). Then just "sudo apt-get update && sudo apt-get dist-upgrade" (if you don't have KDE installed, install meta-package kubuntu-desktop). Let's hope there's no conflicts, otherwise you have to use dpkg forcing in order to get it fully installed. I had some conflicts long time ago when two packages wanted to set the same icon. Let's just assume everything gets installed without problems. :)

Kdesu is equivalent for gksudo, sudo is just fine when you do it from command-line. If you want to run GUI with sudo, kdesu is what you're looking for in KDE. I have no experience with Adept, sorry.

---

### Post by canadianwriterman on 2005-12-14
[QUOTE=artnay]Add Kubuntu.org's 3.5 repo and key, details [here]("http://kubuntu.org/announcements/kde-35.php"). Then just "sudo apt-get update && sudo apt-get dist-upgrade". Kdesu is equivalent for gksudo, sudo is just fine when you do it from command-line. If you want to run GUI with sudo, kdesu is what you're looking for in KDE. I have no experience with Adept, sorry.[/QUOTE]

Thanks for your help, artnay.

---

### Post by anil_robo on 2005-12-14
a moderator named AYSIU has made a good guide to this. Search for his name and KDE and you'll get it.

---

### Post by shakin on 2005-12-14
You can install the Ubuntu update manager in Kubuntu. It won't run in the system tray like in Ubuntu (well, maybe you could do that if you wanted, I haven't tried), but it's easy enough to run it once a day.

---

