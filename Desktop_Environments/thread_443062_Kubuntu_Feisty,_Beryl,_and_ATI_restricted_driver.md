---
title: "Kubuntu Feisty, Beryl, and ATI restricted driver"
date: 2007-05-14
forum: Desktop Environments
---

### Post by trishacupra on 2007-05-14
Hi,

I just decided to ditch Gnome for KDE, because I pushed Gnome to the limits and wanted more in terms of customization.

I had Beryl installed in Gnome. I have a stupid ATI graphics card, which means I downgraded Beryl and need to use the restricted driver to get Beryl to work.

I installed Beryl in Kubuntu, but it's not working well - ie. you can't see the title bar, move the window, etc. I had the same problem in Gnome before installing the ATI restricted driver.

After ages of searching, I can't figure out how to enable the restricted driver in Kubuntu, if it's even possible. I don't know how to check that it even IS enabled. 

If the restricted driver is enabled via Gnome, should it be automatically enabled in Kubuntu?

What should I try?

Thanks,
Trisha

---

### Post by adampyre on 2007-05-14
Hey Trisha,

I am in the same boat as you at the moment. I just switched from GUBUNTU ;) to KUBUNTU. I am attempting to set up Beryl as well. I will reply here if I have any luck.

- Adam

---

### Post by trishacupra on 2007-05-19
Any luck, Adam?

---

### Post by adampyre on 2007-05-19
Actually, I reformatted my HD and went back to GUBUNTU. I don't know if it's just because I started out on it, but after working with it for a week, I didn't like KUBUNTU at all. After 2 days I have GUBUNTU running gnome with beryl very smoothly with minimal issues........ I also tried openSUSE and Knoppix which are both KDE by default. I had even more trouble with openSUSE, but KNOPPIX seems pretty stable in KDE and comes with Beryl pre-installed.. if you really like KDE than I might recommend trying Knoppix: knopper.net (choose your language, I think it is in German by default) otherwise if you need Ubuntu, I might recommend Gnome to qulch any problems......

sorry I couldn't be more help!

---

### Post by trishacupra on 2007-05-19
Thanks Adam. I've been enjoying using Kubuntu without Beryl. But I do prefer Nautilus to Konqueror. I like eye candy but I find myself removing things anyway when the novelty wears off.

I'll have a look at Knoppix, but I'm getting to the point where I've got Kubuntu pretty set up for myself, and I don't really want to change yet again...

Maybe I'll go back to Gnome. Maybe if there's a way to reset all the default settings, because I made it look pretty messy before I started using KDE, and I'd like a clean slate. I suppose removing the gnome desktop completely and reinstalling it would work, but that's another thread, I guess. :)

---

### Post by penkie on 2007-05-19
I am also relatively new. I have installed Kubuntu, but I have "ATI binary X.Org driver" in my adept installer (under System). Furthermore, I installed Emerald Theme Manager to enable nice themed window decorations in Beryl. Before I installed that, window decorations also didn't work here. Maybe you can try that?

---

### Post by trishacupra on 2007-05-19
That sounds like it would work. I didn't look there. I'll give it a try and report back. Thanks!

---

### Post by trishacupra on 2007-05-19
I don't seem to have anything like that. Sigh.

---

### Post by penkie on 2007-05-19
Ow, ok. Maybe it got there as a side-effect of installing the restricted mediaformats.

Look at your /etc/apt/sources.list file. 

I have the following sources enabled (deleted all comments):
```

deb http://nl.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty main restricted
deb http://nl.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://nl.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty universe
deb http://nl.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty multiverse
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```
I guess it should be in one of those repositories or I shouldn't see that particular package. ;)

---

### Post by trishacupra on 2007-05-19
Okay, I'm adding this bunch of repos now.

---

### Post by penkie on 2007-05-19
Ok. Maybe you should also read [this part]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") of the ubuntu guide about adding repositories.

Good luck. :)

---

