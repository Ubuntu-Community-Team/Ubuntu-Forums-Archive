---
title: "Graphical artifacts in Plasma Desktop 5.5.5 on Kubuntu 16.04.1"
date: 2016-08-04
forum: Desktop Environments
---

### Post by physecfed on 2016-08-04
This is a pretty baffling issue, and I've had no luck Googling it, so I apologize in advance if there happen to be forum posts on the subject - I haven't been able to find them.

I'm working off of a new install of Kubuntu 16.04.1 that is currently less than 8 hours old, and the issue is that KDE Plasma Desktop has these strange artifacts that appear in pop-up fields, text entry fields, or other areas. Here's an example when right-clicking on the desktop:

[IMG]https://s31.postimg.org/7bv61zvnf/Screenshot_20160804_025711.png[/IMG]

This also occurs on text entry, so random artifacts will appear and obfuscate text that I'm in the process of typing, along with other assorted nuisances. I wouldn't be too concerned with this bug, if it weren't so hard to track down and so ubiquitous. I've tested 3 other distributions' KDE varieties (CentOS 7, OpenSUSE Leap 42.1, and Fedora 24) and the bug occurs in all of them, so at this point it's either a KDE-wide thing, or it's some unique iffiness with my hardware, and I'm leaning towards the latter because in the case of the former, I thought I'd find more on this issue.

The hardware in question is a HP Z440 workstation, 6-core Xeon CPU, 16GB of RAM, and a Nvidia Quadro K2200 graphics card. Attempts to install the .run driver file provided by Nvidia have been met without positive results (when I stop X11 the window goes blank and I cannot continue with installation, no matter what I try), and in the case of testing the prior distributions, using the CentOS/Fedora repositories' kmod-nvidia driver did not alleviate the issue, so it doesn't immediately seem to be a driver issue.

Regular Unity Ubuntu and GNOME distributions render fine with no errors or glitches. 

Any idea what this could be or how to fix it? The only thing that I've done to this installation so far is apt-get update and upgrade, so in every other respect it's fresh. I am looking forward to being able to get to work, though. If anyone needs any more screenshots of the issue in action, I can try to see about capturing text entry.

Thanks in advance,
physecfed

---

### Post by mook765 on 2016-08-04
Did you try different themes ?

---

### Post by physecfed on 2016-08-04
> **mook765 said:**
> Did you try different themes ?

Yes. The artifacts, both on menu and application features and text entry areas, remain there regardless of what theme is set.

---

### Post by mook765 on 2016-08-05
Here is some information about that
> 
[http://community.kde.org/Plasma/5.5_Errata](http://community.kde.org/Plasma/5.5_Errata)
 

---

### Post by physecfed on 2016-08-07
> **mook765 said:**
> Here is some information about that

That would be fine, if I was running an Intel GPU. As noted in the OP, this is a Quadro machine with a Xeon model that doesn't have an integrated GPU.

My solution in the interim is going to be to roll the machine back to the default Unity distribution and monitor this bug - when it resolves, I'll reconsider the KDE environment, but the current rendering issue renders critical work almost completely infeasible.

---

