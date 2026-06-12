---
title: "Having two package managers"
date: 2009-01-03
forum: Desktop Environments
---

### Post by Freedom65 on 2009-01-03
I have just switched to kubuntu to try it out.I like everything but I had to install Firefox because my comcast webmail did not work with konqueror.I installed firefox with adept and it came with alot of extra packages including synaptec package manager.I don't know if firefox needs synaptec to auto update itself.Anyhow my question is will the system keep using adept for it's updates like I want it to, or will the two programs conflict with each other? Oh by the way I have been using Linux for only 3 months and I don't think I will EVER go back to microsoft!

---

### Post by jamesrl on 2009-01-03
adept, synaptic, aptitude, gnome-apt, dselect, wajig, (and apt-get) are all different front ends for the same package managing system of apt.  So you can use all of them together without problems/conflicts.

EDIT: Technically apt-get is the real thing and the others are front-ends for it, though some such as aptitude have a few fancier features.

---

### Post by abn91c on 2009-01-03
In kubuntu adept will be the **default updater**, no conflicts to worry about, consider it an extra manager

---

### Post by jamesrl on 2009-01-03
Firefox depends on the following packages (for me running intrepid 64 bit):
> Depends: fontconfig, psmisc, debianutils (>= 1.16), xulrunner-1.9 (>= 1.9.0.1), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4),
         libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.14.1), libnspr4-0d (>=
         1.8.0.10), libpango1.0-0 (>= 1.21.6), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4), firefox-3.0-branding (>= 3.0.3+nobinonly-0ubuntu1~) |
         abrowser-3.0-branding (>= 3.0.3+nobinonly-0ubuntu1~)

(got from 'aptitude show firefox-3.0').
Synaptic doesn't appear to be one of them ...  Are you sure you didn't select: update-manager, software-properties-gtk, jockey-gtk, xubuntu-desktop, ubuntustudio-desktop, ubuntu-mobile, ubuntu-mid, gnome-main-menu, gnome, gapti, education-desktop-other, education-desktop-gnome, brdesktop-gnome, aptoncd, apt-watch-gnome, ubuntu-desktop, software-properties-gtk, libeel2-2, language-selector, gnome-app-install, apturl (which synaptic lists for me as packages that are dependent on synaptic)?

---

### Post by Freedom65 on 2009-01-03
I used Adept package manager,checked the Firefox 3 box everything else was automatically added.:)

---

