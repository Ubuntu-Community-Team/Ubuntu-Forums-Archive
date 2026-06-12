---
title: "Backing up .deb files in Synaptic..."
date: 2005-12-31
forum: General Help
---

### Post by Killerah on 2005-12-31
Hi there, installing the kernel update messed up my grub install somehow, and didn't back up my old menu.lst file, so now I can't make it work right again (it removed the windows entry, and I always get some "ntldr is missing" error now). So anyway, I was thinking of just starting over clean, I just don't want to have to re-download everything, so I was wondering if there is some way in Synaptic to backup packages and install the ones that you have sitting on the hard drive (for when I've re-installed). Also, somehow KDE isn't acting right, so I decided I'd install kubuntu because I like KDE better (decided I'd give gnome a shot with ubuntu). So I guess I want to know if kubuntu come with Synaptic too, or does it use some other app?

Thanks
Nate

---

### Post by Sutekh on 2005-12-31
[QUOTE=Killerah]Hi there, installing the kernel update messed up my grub install somehow, and didn't back up my old menu.lst file, so now I can't make it work right again (it removed the windows entry, and I always get some "ntldr is missing" error now). So anyway, I was thinking of just starting over clean, I just don't want to have to re-download everything, so I was wondering if there is some way in Synaptic to backup packages and install the ones that you have sitting on the hard drive (for when I've re-installed). 
[/QUOTE]

This link will show you how to archive all your packages
[Q: How to backup/restore downloaded repositories cache?]("http://www.ubuntuguide.org/#backuprestoredownloadedrepositoriescache")

They'll be in a big fat .tar files that you can extract onto a fresh install, and save you downloading alot of them again.

[QUOTE=Killerah]
Also, somehow KDE isn't acting right, so I decided I'd install kubuntu because I like KDE better (decided I'd give gnome a shot with ubuntu). So I guess I want to know if kubuntu come with Synaptic too, or does it use some other app?

Thanks
Nate[/QUOTE]
kubuntu uses 'Aptitude', which I believe works very similar to Synaptic, they both use apt-get, so the packages you backup can still be used.  You could always install Synaptic in KDE too, if you want to continue to use it.

---

### Post by jdong on 2005-12-31
Actually, KUbuntu 5.10 uses a new GUI called "Adept", which is just as friendly (if not more) than Synaptic. KDE also sports another GUI called "KPackage", which is more mature but less user friendly (it is a generic frontend for KDE and most popular distros)

---

### Post by Killerah on 2006-01-01
Ah, so apparently I should have done a quick search. Well thanks for being noob-friendly around here, you guys all seem like very nice knowledgeable folks. I look forward to installing kubuntu instead of the standard version now. Oh, and also, if I just copied my home directory would I have most (or all) of my settings once all my packages are installed?

---

### Post by jdong on 2006-01-02
[QUOTE=Killerah]Ah, so apparently I should have done a quick search. Well thanks for being noob-friendly around here, you guys all seem like very nice knowledgeable folks. I look forward to installing kubuntu instead of the standard version now. Oh, and also, if I just copied my home directory would I have most (or all) of my settings once all my packages are installed?[/QUOTE]
Yes, you would, but note that Kubuntu, being KDE based, will use somewhat different software than Ubuntu (GNOME), so some settings, like themes and screensavers, need to be reconfigured.

---

