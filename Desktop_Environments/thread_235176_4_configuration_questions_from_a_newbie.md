---
title: "4 configuration questions from a newbie"
date: 2006-08-12
forum: Desktop Environments
---

### Post by Malagise on 2006-08-12
Hello, I am a new Kubuntu user (6.0.6.1). I was drawn to Ubuntu for its ease of "out of the box" use - and I decided I liked KDE better than Gnome. I am very much a newbie and I have a number of questions - I tried finding an answer to them online for about an hour, but, obviously, without success.

1. Kubuntu = (Ubuntu - Gnome) + KDE? While "KDE" seems what I am running (from the looks of it), Adept tells me the kde package is not installed! Could anyone explain me what's happening - how does kubuntu interact with packages designed for kde?

2. Is there a way I can use small buttons on my control panel, so I can fit two rows of them instead of one (the way application tabs fit)?

3. Is there a way to configure Konqueror so that when ctrl+F to find a string in the current page, I do not get a window but instead a small dialog box at the foot of Konqueror (Firefox style)?

4. Is there a way to make my 4+ virtual desktops "contiguous" so that, if I shift a window to the extreme right of desktop 1 so that only half of it remains visible on desktop 1, the other half appears at the extreme left of desktop 2 (to the right of desktop 1)?

---

### Post by meng on 2006-08-12
kde is a metapackage, that is, an empty package which has a host of other packages as dependencies. kubuntu-desktop is another metapackage, including KDE and applications, which is standard issue with Kubuntu.

---

### Post by nalmeth on 2006-08-12
> 1. Kubuntu = (Ubuntu - Gnome) + KDE? While "KDE" seems what I am running (from the looks of it), Adept tells me the kde package is not installed! Could anyone explain me what's happening - how does kubuntu interact with packages designed for kde?
You are running an kubuntu configured and packaged version of KDE. The one you're seeing is the straight KDE.
>  2. Is there a way I can use small buttons on my control panel, so I can fit two rows of them instead of one (the way application tabs fit)?
Right-click panel -> Add applet to panel -> Quick Launcher. You can configure it to have your own apps instead of your most popular ones.
> 3. Is there a way to configure Konqueror so that when ctrl+F to find a string in the current page, I do not get a window but instead a small dialog box at the foot of Konqueror (Firefox style)?
I don't think so..
>  4. Is there a way to make my 4+ virtual desktops "contiguous" so that, if I shift a window to the extreme right of desktop 1 so that only half of it remains visible on desktop 1, the other half appears at the extreme left of desktop 2 (to the right of desktop 1)?
I don't think so... You can do this with XGL/Compiz, and I think Enlightenment can do it, maybe. Not KDE yet

---

