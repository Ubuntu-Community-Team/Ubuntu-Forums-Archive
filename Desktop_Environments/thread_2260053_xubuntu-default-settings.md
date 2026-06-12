---
title: "xubuntu-default-settings"
date: 2015-01-08
forum: Desktop Environments
---

### Post by nep-nori on 2015-01-08
Hi, I'm a newcomer to the forums although I've been using the 'Buntus full-time for around 2 years now.

Basically, I'm going to build up a custom Desktop from the trusty tahr mini.iso (net install is it called?) and I was wondering what exactly is the purpose of xubuntu-default-settings, and for that matter, lubuntu-default-settings, ubuntu-default etc.?

Is it purely cosmetic or are those packages actually useful in some way?

---

### Post by Dennis N on 2015-01-08
According to it's description, xubuntu-default-settings installs all the default settings, artwork, fonts, themes, greeter configuration, and so on for xfce. It's a dependency of xubunutu-desktop. Sounds useful to me.

---

### Post by kerry_s on 2015-01-09
> **nep-nori said:**
> Hi, I'm a newcomer to the forums although I've been using the 'Buntus full-time for around 2 years now.

Basically, I'm going to build up a custom Desktop from the trusty tahr mini.iso (net install is it called?) and I was wondering what exactly is the purpose of xubuntu-default-settings, and for that matter, lubuntu-default-settings, ubuntu-default etc.?

Is it purely cosmetic or are those packages actually useful in some way?

if your building up from the mini.iso, then i would just consider them bloat. just stick to the main apps you want, the 1's to get you up and running in the gui. once you have a running de/wm you can figure out what you want from there. apps will bring in things like icons, themes, etc.. as a dependency, so your going to get a lot of stuff you probably don't want anyways.

---

### Post by nep-nori on 2015-01-11
As I am now typing this from my "vanilla Ubuntu" gotten from the mini.iso, with XFCE4 on top, I'd say xubuntu-default-settings is a useless package.

Thread marked as solved.

---

### Post by kerry_s on 2015-01-11
> **nep-nori said:**
> As I am now typing this from my "vanilla Ubuntu" gotten from the mini.iso, with XFCE4 on top, I'd say xubuntu-default-settings is a useless package.

Thread marked as solved.

congrats on your successful build. i was thinking about doing the same with debian testing or arch.
right now i'm downloading manjaro xfce4 version to try. i'm looking for a nice rolling release setup, not sure what i want the base to be yet.

---

### Post by nep-nori on 2015-01-11
> **kerry_s said:**
> congrats on your successful build. i was thinking about doing the same with debian testing or arch.
right now i'm downloading manjaro xfce4 version to try. i'm looking for a nice rolling release setup, not sure what i want the base to be yet.

thank you. Although I'm about to start a different topic regarding file-roller and xarchiver because I seem to have installed them both somehow (dependencies most likely) and I'd like to know if I can safely axe file-roller without missing functionality.

---

### Post by kerry_s on 2015-01-11
just try it

sudo apt-get purge file-roller

it will ask if you want to proceed

---

### Post by kerry_s on 2015-01-11
i just did a full debian install so i can get use to it
i used the net installer, so i can actually select what ever i want to install. i went with the default for now. it's been years since i last used pure debian. later i'll proably do a custom install.
right now i'm just using the default which is gnome 3 shell, it's like a cheap unity install. lol

---

