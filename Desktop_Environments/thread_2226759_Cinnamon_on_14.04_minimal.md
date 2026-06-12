---
title: "Cinnamon on 14.04 minimal"
date: 2014-05-28
forum: Desktop Environments
---

### Post by billyb351 on 2014-05-28
Hi, I'm currently having some  problems with Cinnamon 2.2 on 14.04.  I'm using  the minimal Ubuntu Trusty install ISO, then building up from there so I  can configure different desktops easily using scripts (i.e. I have some  slow machines that will get LXDE and some fast ones that will get  Cinnamon and I'm debating about whether to leave my file server as  command line only).  I also don't want a lot of the packages that come  standard in Mint or Ubuntu, and I'd rather not remove stuff.  To me,  it (should be) easier to just build it up exactly the way I want.  Since the  stable Cinnamon apt repo for Ubuntu has been removed, I'm currently  building the stable "tagged/released" Cinnamon modules myself, then  creating a local apt repo and installing from there the normal way with  apt-get install cinnamon.  All goes well, the packages seem to be  correct, Cinnamon installs and runs.  However, the themes tab in the  cinnamon settings doesn't work.  It doesn't show any themes.  When I  click the tab "Get more online", then update it, it does its thing, and  appears to load 268 different objects.  None of them show up though in  the window.  It doesn't even show the currently installed and running  theme. In my ~/.cinnamon/spices.cache/ directory I see 268 thumbnail  .png files with the theme pics, and one .json file, so I do believe that  Cinnamon does know about them.  The exact same behavior happens for the  "Desklets", "Extensions", and "Applets" settings.

So being  unable to figure this out, I installed the full Ubuntu with the Unity  desktop.  I pointed apt to my local repo... EXACT same repo on my NFS  file server... never recompiled, never touched the packages then did the  exact same thing: apt-get install cinnamon.  It installed, I rebooted,  chose CInnamon then went to the themes tab.  Now they all show up like I  expect.

Next, I started again with the minimal Ubuntu, then added the official Mint Qiana repo to my sources.list and installed Cinnamon from there.  Identical results... no themes.

Has anybody tried installing Cinnamon on top of a minimal Ubuntu install?  Do you know of any dependencies or packages that might be missing?  Maybe even more general, what are some of the most basic, generic packages that probably should be installed on a minimal Ubuntu install if you do plan on building it up and installing a custom desktop on it?  Right now, I'm installing practically nothing except the basic Xorg stuff, a login manager (gdm) and Cinnamon.

---

### Post by billyb351 on 2014-05-29
Through painstaking analysis (I'll spare you the gory details of how I  looked through source code, dissected working vs. non-working systems,  etc.) I found the problem.  Long story short, a lot of Cinnamon settings  are manipulated through Python scripts.  It uses a Python cairo binding  to do this which is not listed as a dependency for any of the cinnamon  modules.  The package that provides this Python binding is NOT part of a  minimal Ubuntu install, however it does appear in full Ubuntu and Mint  installs.  The package is 'python-gi-cairo'.  So, simply running:
```
sudo apt-get install python-gi-cairo
```
fixed the problem immediately for themes, desklets, applets and  extensions.  They work perfectly after that package is installed.  As  far as I can tell, now everything works as it should.  Perhaps this  should be submitted as a Cinnamon bug?  Hopefully this post may help  someone else out there who likes Cinnamon but wants to build up their  system from scratch.

---

