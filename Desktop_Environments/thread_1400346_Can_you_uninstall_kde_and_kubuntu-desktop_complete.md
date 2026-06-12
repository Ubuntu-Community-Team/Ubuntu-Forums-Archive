---
title: "Can you uninstall kde and kubuntu-desktop completely, then reinstall with KDE 4.4?"
date: 2010-02-06
forum: Desktop Environments
---

### Post by gymophett on 2010-02-06
I have Kubuntu 9.10
I want to uninstall KDE and Kubuntu-Desktop and then only have a cli, and from there install KDE 4.4-Minimal

Is this possible?
What actions would I need to take?
Would I need to add a repository first for KDE 4.4?

(I already know I can do an Ubuntu minimal install and then install KDE, but it won't work on my computer for some odd reason)

Thanks. (:

---

### Post by XubuRoxMySox on 2010-02-06
If the minimal install won't work (and it really is the best way to go for what you're looking for - burn a new CD and make sure the checksum is right), try using Synaptic to *completely remove* the **kubuntu-desktop** and then install **kde-minimal**. You can select packages to install from there (using Synaptic).

-Robin

---

### Post by Crunchy the Headcrab on 2010-02-06
> **gymophett said:**
> I have Kubuntu 9.10
I want to uninstall KDE and Kubuntu-Desktop and then only have a cli, and from there install KDE 4.4-Minimal

Is this possible?
What actions would I need to take?
Would I need to add a repository first for KDE 4.4?

(I already know I can do an Ubuntu minimal install and then install KDE, but it won't work on my computer for some odd reason)

Thanks. (:
Is it possible that the reason an install from a minimal cd won't work is because you are using a wireless internet connection?  There is nothing to control your wireless network on a minimal install, so you need to plug the ethernet cord directly in to your pc, or install a network manager some other way before installing kde.

---

### Post by gymophett on 2010-02-06
> **dixiedancer said:**
> If the minimal install won't work (and it really is the best way to go for what you're looking for - burn a new CD and make sure the checksum is right), try using Synaptic to *completely remove* the **kubuntu-desktop** and then install **kde-minimal**. You can select packages to install from there (using Synaptic).

-Robin

Thanks. 
(I love your avatar btw)
Should I add the repository for 4.4 RC3 first?

---

### Post by gymophett on 2010-02-06
> **Crunchy the Headcrab said:**
> Is it possible that the reason an install from a minimal cd won't work is because you are using a wireless internet connection?  There is nothing to control your wireless network on a minimal install, so you need to plug the ethernet cord directly in to your pc, or install a network manager some other way before installing kde.

I was using an ethernet cable for the install, and checked the MD5 sums. My computer just always shut down during the installation.

---

### Post by overdrank on 2010-02-06
Moved to Desktop Environments

---

### Post by Xbehave on 2010-02-06
> **gymophett said:**
> Thanks. 
(I love your avatar btw)
Should I add the repository for 4.4 RC3 first?
add the [kubuntu beta backports ppa]("https://launchpad.net/~kubuntu-ppa/+archive/beta") as soon as you can (everything should work if you don't but this will save time and bandwidth)

a CLI alternative to synaptic is aptitude (just run aptitude without any options to get the tui)

From minimal CD do:
[LIST=1]
[*]Install root system with nothing and boot into system
[*]Add ppa & update repo,lists (aptitude update / aptitude, press u)
[*]Make sure the aptitude options (aptitude, options>preferences>dependency handling) are set to not install recommends
[*]sudo aptitude install kubuntu-minimal (or use the aptitude tui to do this and review what gets installed)
[/LIST]

From existing install:
[LIST=1]
[*]Add ppa & update repo,lists (aptitude update / aptitude, press u)
[*]Make sure the aptitude options (aptitude, options>preferences>dependency handling) are set to not install recommends
[*]Use the aptitude tui to install kubuntu-minimal, remove kubuntu-desktop, review the updates (maybe do manual pruning of stuff that isn't autoremoved when you remove kubuntu-desktop)
[/LIST]

---

