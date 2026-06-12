---
title: "Unity mode issue with 14.04 as a VM in Windows 8"
date: 2014-04-20
forum: Desktop Environments
---

### Post by alex186 on 2014-04-20
Hello, just finished installing 14.04 as a VM in VMware Workstation using Win 8 as a host. I'm trying to enter Unity mode to give it a go but I get the following error message (see attached picture). I've installed VMware tools so I do not believe that's the issue. Any suggestions? Is it even supported for Win 8?

---

### Post by olliemonster on 2014-05-14
Hi alex
Please could you say what resources the virtual machiene has as that may be the reason vmware was complaining that you couldn't start unity.

---

### Post by alex186 on 2014-05-28
Sure. Could you please let me know where I can find said resources :-) The only resources that I could find are here.

---

### Post by Thomas6818 on 2014-09-07
From the screen shot you posted, you were running [Ubuntu Unity Desktop Environment]("https://unity.ubuntu.com/"). It happens that the "Unity" mode and the name of the desktop environment share the word "unity". Many have the problem of switching to the Unity mode when Ubuntu is running the Unity Deskop environment. 

A solution [here ]("http://notesofaprogrammer.blogspot.com/2014/09/ubuntu-1404-trust-and-vmware-unity-mode.html")suggests that you should switch to a different desktop environment that works with the Unity mode.

---

### Post by dragon-788 on 2015-03-02
I can attest that the blog post linked does work. I've also tested it on the window managers he used as well as some others, and most of them worked pretty well, though KDE had some weird behaviors.

---

