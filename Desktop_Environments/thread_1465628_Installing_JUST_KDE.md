---
title: "Installing JUST KDE"
date: 2010-04-29
forum: Desktop Environments
---

### Post by Jguy on 2010-04-29
Hello,

I want to install JUST KDE. I do not want all of the extra packages with it (same goes with GNOME), such as GIMP, Firefox, Konquerer, empathy, etc. Do I have to build from source, or is there an apt-get method of doing this? I saw somewhere that you can just install kde or kde-base, but neither of those work with the 9.10 source pacakages. 

If I do have to build from source (which I'd actually almost prefer to do), what source packages from [http://www.kde.org/info/4.4.2.php](http://www.kde.org/info/4.4.2.php) do I actually have to download and compile?

Essentually, I want a system similar to LFS that I can add my own packages to and not have to deal with all the packages that I'll never use.

Thanks for any insight you can provide.

---

### Post by keljaden on 2010-04-29
You can use arch linux, or gentoo...or perhaps the kubuntu "alternate" install disk.  You can easily uninstall everything your do not need as well.

---

### Post by Untitled_No4 on 2010-04-29
Or you can try to install kde-minimal from the repositories instead of kubuntu-desktop.

---

### Post by th5th on 2010-04-29
Check out this thread. Do a thread search for KDE. It has some good stuff about what you can/cannot skimp on...

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by Jguy on 2010-04-29
keljaden: no you can't, not easily, that is. It's much more effecient to start with something like server edition and add to it. not start with all the boatware and attempt to subtract stuff.

Untitled: I thought the name of the pkg was just 'kde' or 'kde4', I will try this. thanks!

th5th: thanks for the tutorial. I found something similar but it did not work for me for whatever reason, I probably forgot to add a repository to it. Thanks for the link and I will attempt to check out more. I first have to actually get 10.04 on my machine.

Thanks again.

---

### Post by krazyd on 2010-04-30
> **Jguy said:**
> Hello,

I want to install JUST KDE. I do not want all of the extra packages with it (same goes with GNOME), such as GIMP, Firefox, Konquerer, empathy, etc. Do I have to build from source, or is there an apt-get method of doing this? I saw somewhere that you can just install kde or kde-base, but neither of those work with the 9.10 source pacakages. 

It's very simple:
[LIST=1]
[*]boot using alternative install disk, select "Install command-line system." and install as per normal.
[*]sudo apt-get install kde-minimal
[/LIST]

You just need to make sure you have networking (there is no graphical network-manager client on a command-line system obviously). So either have the machine online via ethernet or know how to use ifconfig/iwconfig.

---

