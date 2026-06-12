---
title: "How do I use the dedicated ubuntu's GRUB and not the wubi one?"
date: 2009-01-09
forum: General Help
---

### Post by chinga on 2009-01-09
I've successfully moved my wubi installation (from hd0) to a dedicated partiton on another harddrive (hd1,0) and it starts fine. But in order to boot it I use Windows XP's bootloader and choose the wubi ubuntu installation. Grub then pops up and in there I choose the entry for my dedicated partition (and it works fine).

I have not yet uninstalled the wubi ubuntu installation in Windows, because as far as I can understand the wubi mbr is needed to load up grub in order to boot the dedicated partition. Is this true?

How do I make the Ubuntu entry in Windows XP's boot loader point to the correct hard drive and partition?

I looked at the following thread but it didn't do me any good:
[http://ubuntuforums.org/showthread.php?t=1033456](http://ubuntuforums.org/showthread.php?t=1033456)

I know I could "just" reinstall Ubuntu on the dedicated partition but I've spent a lot of time configuring it and making it work with my IBM T60 laptop and I don't want that to have been a waste of time :-| Besides... I've become stubborn! :D

---

### Post by mikewhatever on 2009-01-10
You seem to be asking two contradictory questions:

> How do I make the Ubuntu entry in Windows XP's boot loader point to the correct hard drive and partition?

How do I use the dedicated ubuntu's GRUB and not the wubi one?

I can only offer a suggestion to the second one. In order to use the dedicated GRUB, it needs to be installed to the MBR. You can do it from Ubuntu installation CD.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start)

---

### Post by chinga on 2009-01-10
Yeah, apparantly I do ask two questions. But I found some usefull stuff on the page you've linked to. Answers to both my questions actually :-) Thanks.

---

