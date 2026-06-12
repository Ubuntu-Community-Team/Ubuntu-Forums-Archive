---
title: "Moka Icons for Android Studio and Netbeans?"
date: 2014-11-18
forum: Desktop Environments
---

### Post by justin.rixx on 2014-11-18
Hello all! I've been using the Moka icon theme with Unity, and it's great! I love it. But I have a quick question. I installed udtc (Ubuntu Developer Tools Center) and installed Android Studio through that, but the icon that is used isn't Moka, it's the standard icon. And similarly, I installed Netbeans 8.0 from their website (the one in the software centre is i bit outdated) and I'm stuck with the stock icon there as well.

I know that Moka has icons for both ([https://github.com/moka-project/moka-icon-theme/blob/master/src/N/netbeans.svg](https://github.com/moka-project/moka-icon-theme/blob/master/src/N/netbeans.svg) and [https://github.com/moka-project/moka-icon-theme/blob/dfcef1c47eb62f1ec338770567513dea74aa712e/src/A/android-studio.svg](https://github.com/moka-project/moka-icon-theme/blob/dfcef1c47eb62f1ec338770567513dea74aa712e/src/A/android-studio.svg)) But I don't know where to start to get them to play nice with Unity. I'm running Utopic, pretty much stock besides having installed the Moka icons and some developer tools (Oracle Java 8 etc.) I'm fairly comfortable doing command line stuff; it doesn't scare me, I just don't know where to start looking to find this out.

Thanks for taking time to read, and I hope you all have a fabulous day!

-Justin

---

### Post by justin.rixx on 2014-11-18
Feel a little foolish, but after some digging, here's my answer; I had to edit the .desktop files, but I didn't know where they were to edit them. Found a post of askUbuntu, which states that it can be done by running:

gedit ~/.local/share/applications/name.desktop

And it worked, I just changed the icon to /usr/share/icons/Moka/96x96/... and all is well. Hope that can help someone else with a similar issue!
-Justin

---

