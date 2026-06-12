---
title: "KDE &amp; welcome screen for ubuntu"
date: 2008-08-11
forum: Desktop Environments
---

### Post by atyar on 2008-08-11
I'm a seasoned IT Professional, but I'm relatively new to Linux and very new to Ubuntu.  I installed Ubuntu in my home pc on a   2nd hard drive, right alongside XP, and that went pretty smoothly.  Once I got the ip address info configured properly for my Pix firewall and DSL, the rest was easy.  

Couple of questions though - I 'installed' the Kubuntu add-on, but it doesn't appear in the initial 'boot list' or whatever, where I can choose linux, linux safe mode if I recall correctly, or XP.  Is this where I'm supposed to see it, or elsewhere?

Also, is there a way to enable a similar welcome screen to XP, whereby my wife will be able to just click on her user icon and enter a password, versus the Win2K style logon where you have to enter your username?  Thanks!

---

### Post by .nedberg on 2008-08-11
On the login screen you can select Session type, select Kubuntu/KDE here.

I think you can enable that kind of login screen under System -> Administration -> login window. Local tab, Style -> * with face browser.

I am not a Ubuntu user (I prefer Kubuntu) so this last hint might be wrong.

---

### Post by atyar on 2008-08-11
Thanks - I'll probably use kubuntu though, which was my first question.  Does kubuntu use a welcome screen like I'm after, or does it have the option at least?

---

### Post by .nedberg on 2008-08-11
As I use auto login I am not sure what Kubuntu uses by default. Kubuntu with KDE4 has the login screen you want though.

Attached is a screenshot of the login screen in KDE4.

Simply installing kubuntu-desktop or kubuntu-kde4-desktop will not change the login screen, you will still use GDM (GNOME), and I am sure GDM has this behaviour too, I am just not sure how to enable it...

If you however install kubuntu-desktop you should be given the choice to use KDM.

---

### Post by edog76 on 2008-08-11
Sounds like gdm is the current login screen. You can switch to kdm by entering a terminal and typing:
```
sudo dpkg-reconfigure gdm
```
This will then prompt you to select either gdm or kdm as the default login screen. The kdm login (3.5 and up) is Windoze style and you can enter the password for the default login ID, or mouse-click (etc.) for others then enter the password. I would restart the computer after making the change.

---

### Post by Xiong Chiamiov on 2008-08-11
BTW, if you hadn't gotten the Kubuntu vs. Ubuntu thing cleared up, Kubuntu is really just Ubuntu with KDE installed instead of GNOME.  GNOME and KDE are the two most popular Desktop Environments, which essentially define the way you interact with your computer.  The underlying core of Ubuntu, however, is the same; you just choose to run one or the other of the DEs on top of it.

In fact, you can actually run both at the same time, if you wish.  If you're in KDE, K -> switch user (mm, that's KDE4, I think it's K -> sessions or something?) you can start a new X session, from which you can choose GNOME (or whatever) at the login screen.  You can then switch between them with ctrl+alt+f6 and 7, I believe.

---

