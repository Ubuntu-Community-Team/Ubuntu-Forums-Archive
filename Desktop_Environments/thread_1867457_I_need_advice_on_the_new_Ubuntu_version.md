---
title: "I need advice on the new Ubuntu version"
date: 2011-10-23
forum: Desktop Environments
---

### Post by Sean Hayes on 2011-10-23
So, I hear there's some major changes to Ubuntu 11.10. With 11.04 I've been using the GNOME classic desktop, which I'm told will no longer be present. I briefly tried Unity with 11.04 but found it mostly unusable for my needs, but I hear there have been some improvements. I'd like to know if there's any way I can implement some of my current desktop setup into the new version.

1. I currently have a top panel with custom application launchers on it and a drawer with custom Firefox launchers in it, each one set to a different profile (I use different profiles for browsing, web dev, extension dev, etc.).

2. I have an autohiding panel on the right side of the screen which has GNOME widgets for displaying CPU, memory, disk, and network usage and hardware temperature.

Is there any way to set this stuff up in Ubuntu 11.10?

---

### Post by W.McL on 2011-10-23
If you didn't yet downgrade to 11.10, don't do it. (Yes, this so called "upgrade" is a DOWNgrade usability wise) 

The Gnome fallback session, which is available in 11.10 after installing gnome-panel is lightyears away from Gnome2's usability, basically the indicator applet is broken, and you need at least 2 clicks more than before to achieve asimple task like configuring your printer.

Best stay with 11.04 until the gnome fallback session has been fixed and actually works (if that ever happens), or wait for the [upcoming fork of good old Gnome 2]("https://github.com/Perberos/Mate-Desktop-Environment") to become ready.

---

### Post by Shazaam on 2011-10-24
I haven't gone the UPGRADE route so I can't give advice on what will work and what may get broken.

For me, I still wanted Ubuntu and a way to have some adjustability without having to jump through hoops to get it. So I installed Xubuntu 11.10 to a separate partition. It has a (short) learning curve but it's not impossible to figure out. At login you can choose the xubuntu desktop, which give you a gnome-similar xubuntu session, or a full xfce session (albeit Ubuntu customized). If you get tired of it you can always install ubuntu-desktop to get all of that gnome goodness.

Screenshot...
[http://ubuntuforums.org/attachment.php?attachmentid=205078&d=1319223681](http://ubuntuforums.org/attachment.php?attachmentid=205078&d=1319223681)

---

### Post by lincoln32 on 2011-10-24
done both a upgrade from 11.04 to 11.10 and 6-7 clean 11.10 installs so far
and no failures other that the normal new release bugs but overall I love 11.10 better than 11.04 and bugs were all minor things flash issues and some laptop button issues and one that had the screen dim while booting till it was up then worked fine. My 2 cents are it works way better than 
installs of older versions but unity does take a while to learn and should be totally debugged by 12.04 and I have learned to use unity and starting to really love it:KS

---

### Post by typhoon_tip on 2011-10-24
> **Sean Hayes said:**
> So, I hear there's some major changes to Ubuntu 11.10. With 11.04 I've been using the GNOME classic desktop, which I'm told will no longer be present. I briefly tried Unity with 11.04 but found it mostly unusable for my needs, but I hear there have been some improvements. I'd like to know if there's any way I can implement some of my current desktop setup into the new version.

1. I currently have a top panel with custom application launchers on it and a drawer with custom Firefox launchers in it, each one set to a different profile (I use different profiles for browsing, web dev, extension dev, etc.).

2. I have an autohiding panel on the right side of the screen which has GNOME widgets for displaying CPU, memory, disk, and network usage and hardware temperature.

Is there any way to set this stuff up in Ubuntu 11.10?

1. I haven't checked deeply, but there should be something. Or you can add all your stuff to the Unity launcher bar on the left as I did.

2. You can have all those widgets by adding to your top bar, near the clock. I have all of those including a weather widget. The most nice thing is that they stay perfectly spaced and sorted out, altough you cannot change the order of them. I also have a CPU scaling controller, useful sometimes to burst CPU to maximum performance permanently. This is for 11.04, but works well on Unity and 11.10 as well (attention: some widgets need to be started manually from command and then added to autostart in order to start at logon ! [http://news.softpedia.com/news/Top-10-Ubuntu-11-04-Unity-Panel-Applets-208034.shtml](http://news.softpedia.com/news/Top-10-Ubuntu-11-04-Unity-Panel-Applets-208034.shtml))

---

