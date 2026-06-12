---
title: "questions (boot,app, and kde desktop)"
date: 2009-04-03
forum: General Help
---

### Post by flyingsliverfin on 2009-04-03
right.

I think all of the problems are inter-related. I installed the kde desktop, but after that it installed all of these kde apps in my ubuntu system that I don't want. how can I un-install the kde desktop and all the apps that came with it. I think this is related too. It doesn't matter as much, but when I boot up, it should show the UBUNTU and then the little orange bar underneath it. However, it is all blue and says Kubuntu, when I am fairly sure that my os is ubuntu.

Another issue, the one that some random KDE app is starting all of my openoffice files, I think is fine if I set Open office to be default. How do I do this?

---

### Post by LoloftheRings on 2009-04-04
To remove the applications you don't want/need, go to Applications -> Add/Remove or in KDE Start Menu-> search for adept
In Adept or the Add/Remove program, uncheck all applications you don't want and apply.
These are packages that come with KDE, GNOME has a lot of these applications too, such as Brasero, Rhythmbox, Pidgin.

The blue Kubuntu loading screen is also automatically installed with KDE. In GNOME, you can reset it to default like this:
```

sudo apt-get install startupmanager

```
This will install a little GUI app to configure the boot screens.
Now, go to System -> Administration -> StartUp-Manager -> Appearance
Set the Usplash theme to usplash-theme-ubuntu

Not sure about the last issue..

Sorry for explaining everything in GNOME ;)

Hope this was all clear.. Good luck

---

### Post by flyingsliverfin on 2009-04-04
so there is no direct way of un-installing the kde desktop (the command I used to get it was sudo apt-get install kde-desktop, or something like that)

otherwise thank you

---

