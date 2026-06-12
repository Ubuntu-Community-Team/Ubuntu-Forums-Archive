---
title: "Installed new graphics card. Startmenu gone?"
date: 2013-04-02
forum: Gaming &amp; Leisure
---

### Post by sshaddoww on 2013-04-02
Yesterday I decided to use an old Ati graphics card that has 30 watts in  idle (2D) consumption instead of over one hundred watts (the Nvidia I  have been using). The graphics card is is working and I started my  Ubuntu 12.10. But after login I did not see my Startmenu anymore. The  same problem as before (linkt to [thread]("http://ubuntuforums.org/showthread.php?t=2127131"). I am currently in my old Ubuntu 12.04 LTS  installation that I have on a separate harddrive. 

So what should I do to  fix my Startmenu back and get Ati drivers instead of Nvidia?

---

### Post by ManamiVixen on 2013-04-02
What card is it? If it is too old, you may not be able to use it. ATI dropped support in their proprietary driver for all their graphics cards older than, and including the HD 4000 series cards. Also, you will have to remove the Nvidia driver too in order to install the ATI driver if possible.

Edit: The built-in open source ATI driver tends to work well, but it is finicky and not energy efficient. You my be better off on the Nvidia Card.

---

### Post by Perfect Storm on 2013-04-02
I agree with ManamiVixen.
Also if you want to use Steam it's highly recommendable that you use that Nvidia instead of the old ATI card.

---

### Post by oldrocker99 on 2013-04-02
> **Artificial Intelligence said:**
> I agree with ManamiVixen.
Also if you want to use Steam it's highly recommendable that you use that Nvidia instead of the old ATI card.

Absolutely. I upgraded my old nVidia 520 to the 650ti (the Boost model, of course, came out after I'd installed...), and Steam is smooth as silk. The opening screen of Crusaders 2 no longer stutters, Trine 2 is actually playable (it gave me a framerate of ~2.5/sec with the 520, which was the lowest-end nVidia card 2 years ago) now, and this graphically-intensive game is like a movie now. The xorg-edgers PPA, which I have used for a couple years now and which I recommend, provides the latest (313.26) nVidia .deb packages.

The xorg-edgers PPA, which provides drivers for ALL graphics cards, is

**ppa:xorg-edgers/ppa**

Give it a try; old ATI cards are consistently being improved by this team.

---

