---
title: "Purge Unity, replace with gnome-core"
date: 2013-09-16
forum: Desktop Environments
---

### Post by Andrew_Lucas on 2013-09-16
Hi all!

I have a friend, who after a brief stint with Linux Mint (first Cinnamon, then KDE), asked me about other desktop environments. I said what he had was a choice between the more traditional "desktop" metaphor, with windows and menus, or something which is a bit more radical like GNOME 3 (personally, I'm a traditionalist). He was interested in trying the new approach, so I suggested he use DistroWatch to find a distribution that was "GNOME-centric". He ended up (for some reason) picking OpenSUSE, but after a few days missed apt and the huge repos of the Debian-based distros. I knew there wasn't a "GNOME 3" Ubuntu release, so suggested he install a standard copy of Raring and then purge Unity.

I knew about the "gnome-core" package, and felt it was probably best to recommend the package with the absolute minimum (given that he would be installing it on top of Unity) required to run GNOME. [Here]("http://packages.ubuntu.com/raring/gnome-core") it recommends "gnome-network-manager", so encouraged him to install that too. He now has a GNOME 3 desktop which he's happy with.

However, not using Unity myself, could anyone give guidance on exactly which packages to purge in order to leave behind *just* GNOME, including any basic utilities which come with Unity, but are basically made obsolete by GNOME's replacement packages? The goal at the end of this is to have as tidy a distro as possible, with one DE, one set of utility programs (e.g. a file manager, GDM rather than LightDM, etc.), which extra packages (which he's capable of installing himself e.g. Java) can be put on top of without any fuss. I did run a Google search before posting, but the main results that were turning up were referring to 12.x, and I'm assuming there have been updates (i.e. extra packages) since then?

Cheers!

---

### Post by ibjsb4 on 2013-09-16
It seems that people that try to remove Unity are only partially successful.  Most find that upon updating there system that Unity gets reinstalled.  Myself, I do not have Unity, just Gnome Classic installed.  My approach was to build from scratch, using the mini.iso.  So instead of having to remove Unity, it simply was never installed on my system.

---

### Post by Andrew_Lucas on 2013-09-16
> **ibjsb4 said:**
> It seems that people that try to remove Unity are only partially successful.  Most find that upon updating there system that Unity gets reinstalled.  Myself, I do not have Unity, just Gnome Classic installed.  My approach was to build from scratch, using the mini.iso.  So instead of having to remove Unity, it simply was never installed on my system.

Yeah, that was my first instinct too. However, partly because he dual boots, and partly because the internet connection here isn't that stable, the installation repeatedly failed. Plus, package management in the CLI is confusing - and for some reason, the default was to install both x64 and x86 packages - I didn't have the patience to go through and remove all the x86 packages one by one. I think there might also have been some conflicts there, when the installer came to put the x64 over the x86 (or vice versa) and couldn't.

As it was, there was some awkward screwing around with the bootloader. Idk why, but attempting to fix GRUB2 via the CLI didn't seem to work (from the live disc: the process was mount root partition, point GRUB to root partition and install GRUB to the MBR). In the end, we ended up using the GUI (is it called Boot Repair or something?). It claimed to have failed, but upon rebooting the computer, GRUB was a) present and b) fully functioning.

I'm going to attempt to try and twist his arm into doing a clean install of Windows some point over the next couple of days. Perhaps reformatting the HDD will remove whatever remnants of files were causing the trouble? Either way, it's a job for another day/week/month, not something immediate which sorts out this issue with Unity.

Maybe it would be best to consider this run as a proof-of-concept, prior to a future clean install of everything?

---

### Post by buzzingrobot on 2013-09-16
Try Ubuntu Gnome.  I'm using it now; works fine.  Here's the wiki: [https://wiki.ubuntu.com/UbuntuGNOME](https://wiki.ubuntu.com/UbuntuGNOME)

I've come across various recipes for removing Unity in order to install a so-called pure version of some other DE.  They're all different, which says something.

---

### Post by Andrew_Lucas on 2013-09-16
> **buzzingrobot said:**
> Try Ubuntu Gnome.  I'm using it now; works fine.  Here's the wiki: [https://wiki.ubuntu.com/UbuntuGNOME](https://wiki.ubuntu.com/UbuntuGNOME)

I've come across various recipes for removing Unity in order to install a so-called pure version of some other DE.  They're all different, which says something.

In the nicest way possible, I do feel your solution is missing the point slightly. We have a working version of Ubuntu with GNOME installed. Downloading another iso (with the less-than-perfect internet connection), reinstalling the system, and going through all the faff of screwing with GRUB again seems a little excessive when it is possible to simply remove the Unity elements, no?

---

### Post by buzzingrobot on 2013-09-16
> **Andrew_Lucas said:**
> In the nicest way possible, I do feel your solution is missing the point slightly. We have a working version of Ubuntu with GNOME installed. Downloading another iso (with the less-than-perfect internet connection), reinstalling the system, and going through all the faff of screwing with GRUB again seems a little excessive when it is possible to simply remove the Unity elements, no?

Nope.  My point is that there is no simple, sure, way of removing Unity.

A few Unity-removal posts are posted at mate-desktop.org.  They pertain specifically to Mate, but they might be a starting point.

---

### Post by VMC on 2013-09-16
> **Andrew_Lucas said:**
> ... I knew there _wasn't a "GNOME 3" Ubuntu release_, so suggested he install a standard copy of Raring and then purge Unity....
This may be what prompted [COLOR=#000000]buzzingrobot to respond, since [UbuntuGNOME]("https://wiki.ubuntu.com/UbuntuGNOME") ***is*** GNOME3, and has been since Raring.[/COLOR]

---

### Post by markbl on 2013-09-16
From a standard Ubuntu desktop install, you don't need to remove Unity and you don't need to install a whole new ISO.

Just "apt-get install gnome-shell" then log out, select GNOME (instead of Ubuntu) session, and log back in again.

---

### Post by grahammechanical on 2013-09-17
I just do not understand how people can get so confused.

Ubuntu is built upon Gnome 3, which by the way is a desktop environment. It has the Unity user interface instead of the Gnome 3 shell user interface. Most if not all of the Ubuntu uilities are Gnome utilities. Network Manager in Ubuntu is in fact network-manager-gnome. Synaptic Package Manager tells me that Nautilus (called File Manager in Ubuntu) is the official file manager for the Gnome desktop. Update Manager is the Gnome apt update manager. System Monitor is gnome-system-monitor. Do I need to go on?


Regards.

---

### Post by buzzingrobot on 2013-09-17
> **grahammechanical said:**
> I just do not understand how people can get so confused.



There's much more to Unity than these standalone Gnome utilities:  The Launcher, HUD, Lenses, Compiz, etc. Removing all that cleanly, and then cleanly installing Gnome Shell, is problematic.

I think the simplest and best way to use Gnome Shell on standard Ubuntu is to just install it, leaving Unity in place.  Some folks don't want to leave Unity in place, but, for them, I'd recommend installing the Ubuntu Gnome distro.

---

### Post by PJs Ronin on 2013-09-18
Might be out of my depth here, but what about installing from a mini.iso with the "--no-install-recommends" option then build from there with something like 'sudo apt-get install gnome-shell gnome-shell-extensions'.

---

### Post by ibjsb4 on 2013-09-18
> **PJs Ronin said:**
> Might be out of my depth here, but what about installing from a mini.iso with the "--no-install-recommends" option then build from there with something like 'sudo apt-get install gnome-shell gnome-shell-extensions'.

[http://ubuntuforums.org/showthread.php?t=2175157&p=12792024&viewfull=1#post12792024](http://ubuntuforums.org/showthread.php?t=2175157&p=12792024&viewfull=1#post12792024)

---

### Post by PJs Ronin on 2013-09-18
> **ibjsb4 said:**
> [http://ubuntuforums.org/showthread.php?t=2175157&p=12792024&viewfull=1#post12792024](http://ubuntuforums.org/showthread.php?t=2175157&p=12792024&viewfull=1#post12792024)

I'll get back in this nice box Mr Schrödinger built for me.

---

### Post by Andrew_Lucas on 2013-09-30
> **buzzingrobot said:**
> There's much more to Unity than these standalone Gnome utilities:  The Launcher, HUD, Lenses, Compiz, etc. Removing all that cleanly, and then cleanly installing Gnome Shell, is problematic.

I think the simplest and best way to use Gnome Shell on standard Ubuntu is to just install it, leaving Unity in place.  Some folks don't want to leave Unity in place, but, for them, I'd recommend installing the Ubuntu Gnome distro.

Yeah, my main concern about Unity (and my friend's) was the much discussed privacy issue. I feel less and less enthusiastic about Canonical as a whole, and use of Unity (or encouraging use of Unity) seems to me to be an acceptance, or even advocacy, of Ubuntu's on-going commercialisation. Hence, leaving it installed is...not an option.

Plus, this might be verging on OCD, but I'm a big fan of building a system from the ground up :D. It seems somewhat tidier - and saves on space and time when it comes to administrating the system (i.e. you don't have to wait for software you don't use to update it - nor do you have it sitting around cluttering your disk and generally making a nuisance of itself).

I didn't know about the Ubuntu GNOME spin, but cheers for mentioning it guys! My friend has now installed that and is using it quite happily (though he has talked of bugs, which K/X/Ubuntu didn't have - I can't remember the details, and he's not especially technically savvy, but it was something along the lines of a particular program hogging resources, then crashing Xserver (at least, that's what it sounded like - the screen going dark, followed by the message "Ubuntu has recovered from a serious error", or words to that affect).

Does anyone have any feelings on Debian? I'm going to open a new thread regarding Ubuntu/Debian differences (basically to confirm what I've read and ask for further info), but I've been toying with the idea of leaving Xubuntu and starting a super minimal install of KDE, as described [here]("http://antreimer.wordpress.com/2012/07/02/debian-with-minimal-kde-simple/"). Presumably it's possible to do the same thing for Debian, and I could upgrade him to jessie (testing), so he has access to some new(er) programs.

---

### Post by Andrew_Lucas on 2013-09-30
> **PJs Ronin said:**
> Might be out of my depth here, but what about  installing from a mini.iso with the "--no-install-recommends" option  then build from there with something like 'sudo apt-get install  gnome-shell gnome-shell-extensions'.


See my post - thinking of doing a similar thing but on Debian?

---

### Post by Andrew_Lucas on 2013-09-30
> **Andrew_Lucas said:**
> Yeah, my main concern about Unity (and my friend's) was the much discussed privacy issue. I feel less and less enthusiastic about Canonical as a whole, and use of Unity (or encouraging use of Unity) seems to me to be an acceptance, or even advocacy, of Ubuntu's on-going commercialisation. Hence, leaving it installed is...not an option.

Plus, this might be verging on OCD, but I'm a big fan of building a system from the ground up :D. It seems somewhat tidier - and saves on space and time when it comes to administrating the system (i.e. you don't have to wait for software you don't use to update it - nor do you have it sitting around cluttering your disk and generally making a nuisance of itself).

I didn't know about the Ubuntu GNOME spin, but cheers for mentioning it guys! My friend has now installed that and is using it quite happily (though he has talked of bugs, which K/X/Ubuntu didn't have - I can't remember the details, and he's not especially technically savvy, but it was something along the lines of a particular program hogging resources, then crashing Xserver (at least, that's what it sounded like - the screen going dark, followed by the message "Ubuntu has recovered from a serious error", or words to that affect).

Does anyone have any feelings on Debian? I'm going to open a new thread regarding Ubuntu/Debian differences (basically to confirm what I've read and ask for further info), but I've been toying with the idea of leaving Xubuntu and starting a super minimal install of KDE, as described [here]("http://antreimer.wordpress.com/2012/07/02/debian-with-minimal-kde-simple/"). Presumably it's possible to do the same thing for Debian, and I could upgrade him to jessie (testing), so he has access to some new(er) programs.

If anyone has any views to add, and would like to continue the discussion in a less specific sense, I've opened a new thread [here]("http://ubuntuforums.org/showthread.php?t=2177880").

---

