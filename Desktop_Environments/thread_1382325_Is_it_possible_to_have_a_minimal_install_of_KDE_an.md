---
title: "Is it possible to have a minimal install of KDE anymore (Karmic/KDE 4.4)?"
date: 2010-01-15
forum: Desktop Environments
---

### Post by tghe-retford on 2010-01-15
I'm currently testing a Karmic/KDE 4.4 with Virtualbox and beforehand when I installed KDE, it used to work by installing from the alternate CD, using the install a command line option and installing this round of packages:

```
kdebase kdm kpackagekit kwin xorg systemsettings kmix oxygen-cursor-theme python-software-properties plasma-desktop
```

This would get a basic install of KDE (with one or two extras) working in the past with no problems, but now trying this with the Kubuntu Karmic KDE 4.4 Beta packages from the Kubuntu Beta PPA (I also noticed this happened with Lucid) will no longer work because plasma-desktop will crash at startup, leaving only ALT+F2 to bring up the run command option as the only way to start and run programs, which isn't ideal for me.

Searching for an answer, the only one I can find is to install kubuntu-desktop, although this defeats the purpose of having a minimal install!

Is it possible to have a minimal install of KDE anymore, or has kubuntu-desktop become an integral part of an install?

Thanks in advance.

---

### Post by Falc7 on 2010-01-15
Try installing ubuntu server, then sudo apt-get install kde-minimal
Then add the ppa for 4.4 and upgrade
This is what i've done and plasma dosen't crash at log in

---

### Post by benerivo on 2010-01-15
There's [kde-minimal]("http://packages.ubuntu.com/karmic/kde-minimal"), which you could try, or look at its dependencies to work what package(s) you're missing from your install.

---

### Post by tghe-retford on 2010-01-16
Nope, kde-minimal got me as far as the wallpaper, but plasma-desktop did not get installed, so no panels, widgets or right click menu on the desktop. Initially, it asked me to install kdebase-workspace-bin, but it was already installed. From my knowledge of changes to KDE 4.4 in Lucid, I had to install plasma-desktop (now as a separate package) to get it to work. Whilst it worked in Lucid, when I tried it now on a fresh install of Karmic in Virtualbox, the desktop just crashed as before.

---

### Post by heminder on 2010-01-16
i'm intrested in this too.
every time i select kubuntu-desktop in synaptic it also picks loads of packages that i don't want.
the biggest offender being openoffice. i can deselect them, but it still has loads of dependency files still selected :S

---

### Post by huviduc on 2010-01-18
I got this working by installing the plasma-desktop package. It doesnt set it up as a seperate session. but you can run it within gnome by typing "plasma-desktop &" in the terminal. This will give you your minimal kde plasma while retaining use of all current running programs and gnome panel. 

Not real sure how to get it running as a seperate session though. KDE is always very unstable for me, so this gives me the gnome envirnment with KDE desktop look. Just a thought for ya

---

### Post by captaincrook on 2010-01-18
I've built a KDE Minimal install (using the kde-minimal package), but this was using the default repos. After that installed, I added the Kubuntu PPA tp update them and its been working alright since then. I haven't dove into the 4.4 pre-releases yet so I can't really help there.

---

### Post by tghe-retford on 2010-01-19
Installing 'kde-minimal' and then going to the desktop, adding the Kubuntu Beta PPA and then 'sudo aptitude update' then 'sudo aptitude dist-upgrade' within Konsole managed to get a minimal KDE 4.4 working when I restarted. Finally! Nice to have a minimalist KDE 4.4 system up and running (if it is in Virtualbox at the moment).

---

