---
title: "Uninstalling a Package"
date: 2008-12-12
forum: General Help
---

### Post by solwic on 2008-12-12
I'm getting ready to update to KDE4.2 and the first step of instructions is to get ride of koffice-data-kde4 package, because of a conflict.  

Problem is, I can't find the package anywhere.  I looked under Applications -> Office and there's nothing there that says koffice underneat it.  I looked in synaptic and adept...nothing.

Is this called something else?  Or is this not something installed with Kubuntu 8.10?  I wouldn't have added it; I use OOo.  

I ran the same Kubuntu install CD in VirtualBox and upgraded it to KDE4.2  I simply ignored the package removal thing, and everything went fine.  I wonder if it's safe to do that this time, or if that means I don't have this package.  

But the instructions come from Kubuntu's website, so I thought I had better be sure.  I DO NOT want to bork something and have to reinstall Kubuntu!

Anybody know?  Thanks!

---

### Post by gettinoriginal on 2008-12-12
hmmmmmmmmmm, koffice **_is_** in my synatptics, not installed, I also use OO, You might want to look again, maybe in terminal do an update, and make sure all your repositories are up to date.

---

### Post by adult swim on 2008-12-12
run from a terminal ```
sudo apt-get remove koffice-data-kde4
``` and it will remove it if is on your system.

---

### Post by solwic on 2008-12-12
> **adult swim said:**
> run from a terminal ```
sudo apt-get remove koffice-data-kde4
``` and it will remove it if is on your system.

Tried that, said package didn't exist.  I assumed that meant I didn't have it, and so went ahead and updated to KDE4.2.  Worked like a ****ing charm.  

BTW, for those KDE users who *haven't* upgraded...do so.  Right now.  You won't regret it.  KDE4.2 is going to be freaking awesome when it releases a full release.  Even in beta it looks bad ***.  :)

OK.  Thanks for the tip!  :)

---

