---
title: "missing kubuntu-base?"
date: 2005-11-18
forum: Desktop Environments
---

### Post by supenguin on 2005-11-18
I initially installed Ubuntu on my computer, and now I want to switch over to Kubuntu without reinstalling. I've read that you should do apt-get install kubuntu-base and kubuntu-desktop.

Well, kubuntu-desktop is installed and seems to be working just fine. However, I can't seem to find kubuntu-base

```
sudo apt-get install kubuntu-base
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-base
```

What am I missing here? Am I missing anything here? As far as I can tell, the only different at this point may be the splash screen saying Ubuntu instead of Kubuntu, but I haven't rebooted since I installed kubuntu-desktop. Even if that's the only difference, I would still like to install Kubuntu-base because I like the nice blue splash screen better than the brown.

---

### Post by incubus on 2005-11-18
Penguin,

Are you sure it's "kubuntu-base" what you want? I've never seen that myself, but I've been far from ubuntu for a while (I was using arch linux).

"apt-cache search kubuntu" gives me this:
kubuntu-desktop - Kubuntu desktop system
kubuntu-docs - kubuntu documentation
kubuntu-konqueror-shortcuts - Konqueror shortcuts for the Ubuntu wiki and bugzilla
kubuntu-live - Kubuntu live system
kubuntu-artwork-usplash - kubuntu artwork for usplash
kubuntu-default-settings - Default settings and artwork for the Kubuntu desktop

If I'm not mistaken, the one for the splash screen is the "kubuntu-artwork-usplash". You could try that one.

---

### Post by supenguin on 2005-11-18
I think you're right... My work computer had Ubuntu installed, and I wanted to switch to Kubuntu without reinstalling the whole system and all the docs I read said install kubuntu-desktop and kubuntu-base. But all that info was about hoary and earlier versions.

I have a Kubuntu system at home, and there is no kubuntu-base. I guess the ubuntu-base is the same as Kubuntu except the artwork or something? Here's the funny thing about this - I tried rebooting, and it doesn't look like the onboard video card my work computer has support the boot splash screen, or at least its not showing up. Oh well, I only reboot for kernel upgrades, so maybe every month or two, if not longer.

---

### Post by N8K99 on 2005-11-19
I'm fairly certain what you want is kdebase, not kubuntu-base.

---

### Post by incubus on 2005-11-19
Yeah, kdebase does exist for sure.

Have you tried to install:
kubuntu-artwork-usplash

If that doesn't work right away, you may need to append something to your GRUB entry for booting. I don't know about this one because I don't use the splash screen myself (I personally dislike).

But try that.

---

### Post by Seth on 2005-11-19
kubuntu-desktop depends on EVERYTHING you need for a proper Kubuntu installation.

---

