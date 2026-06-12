---
title: "Definitely can't install Kubuntu !"
date: 2006-01-10
forum: General Help
---

### Post by benco on 2006-01-10
I have tried to install Kubuntu (at least 10 times !)  but never succeeded. It always fails in the system configuration after reboot while configuring libxt-java. Even tried different CDs, always md5um verified.
So I tried to install Ubuntu and the first attempt was successful.
But I still prefer KDE to Gnome, so I apt-got kubuntu-desktop and things seem to roll smoothly.
I have 3 questions :
Question #1 : why does the installation process freezes on libxt- java ?
Question #2 : is it enough to apt-get kubuntu-desktop over an Ubuntu installation to have a Kubuntu system ?
Question #3 : if I totally want to clean up my system and erase Gnome, how can I do ?
Question #4 : though I prefer KDE, I have found that some things in Gnome are better handled. In particular font rendering. I have tried the 'GTK styles and fonts' tip but Firefox still looks better in Gnome. How can it be fixed ?

Thanks in advance.

---

### Post by Tuf on 2006-01-10
1.) Dunno
2.) I think so, Kubuntu is just Ubuntu with KDE
3.) I think you remove the Gnome Desktop environment with Synaptic
4.) Dunno I havent noticed that before.

---

### Post by harisund on 2006-01-10
If you are ready for a reinstall, you could simply install using the "server" option at the boot line (which would install nothing except some basic components) and then do apt-get install either of kubuntu-desktop, ubuntu-desktop or xubuntu-desktop and you would't be getting any thing else.

---

### Post by SuSUntu on 2006-01-10
[QUOTE=Tuf]<snip>
2.) I think so, **Kubuntu is just Ubuntu with KDE**
<snip>[/QUOTE]

I have read the "bold" statement here and elsewhere many times, and while in theory this makes sense, I have not found it to be correct, at least for my installation.

All kinds of glitchy things happen along the way during installation of Kubuntu that don't happen with Ubuntu, most of which I can't remember now in detail, but most of which I was able to overcome with retries or editing files at the command-line.

However, the deal killer for me and Kubuntu after trying to install it MANY times on the same machine was that no matter what was tried, the network settings could not be retained. DHCP didn't work nor did setting a static IP. Nameservers, gateway and machine IP would all get munged leaving no connectivity; the changing would occur without even rebooting. Entering the info in network set-up dialogs (GUIs) or manually changing the info in text files made no difference. It was very frustrating. I was able to find some users experiencing the same things, but no solution was discovered by me.

I had probably tried installing Kubuntu 5 or six times, failing each time, so it was very surprising to me when installing Ubuntu worked flawlessly. I was so surprised that I went back to trying to get Kubuntu installed, but couldn't. Eventually, I stuck with Ubuntu. I will likely install KDE on top of the Ubuntu installation at some point, but for now I'm fine with Gnome.

But ... based on my experience, I have to say that there are at least some fundamental differences, whether intended or not (they have very different bugs?), between Ubuntu and Kubuntu.

---

### Post by kenweill on 2006-01-10
I like KDE over GNOME.

Im using Ubuntu 5.10. I have tried installing kubuntu-desktop but got me into trouble.

I reinstalled everything, Ubuntu, then instead of installing kubuntu-desktop, i just installed KDE.

And here I am, using KDE on Ubuntu.

---

### Post by benco on 2006-01-10
Thanks for your (quick) replies.
Yes, harisund, I am ready for a reinstall (once again !) if at the end I have a stable system. So I'll try this one.
Based on my personal experience, I tend to agree with SuSUntu who writes that the difference between Kubuntu and Ubuntu is more than just the desktop.
I'll keep on investigating ...

Edit : kenweill, I hadn't seen your post. You just 'apt-get install kde' ?

Does anybody know the difference between 'apt-get install kde' and 'apt-get install kubuntu-desktop' ?

---

### Post by feathers on 2006-01-10
kde just installs kde, whereas kubuntu-desktop installs all packages that the kubuntu team decided belong to kubuntu. This means some more configuration files, and other non kde programs as well. So I would go for kubuntu-desktop.

---

