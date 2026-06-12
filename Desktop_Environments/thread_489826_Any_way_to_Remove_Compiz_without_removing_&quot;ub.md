---
title: "Any way to Remove Compiz without removing &quot;ubuntu-desktop&quot;?"
date: 2007-07-01
forum: Desktop Environments
---

### Post by OzzyFrank on 2007-07-01
I've been trying to figure out what exactly Compiz does, and besides the wobbly windows (which disappeared when I installed Beryl) and desktop cube (that never actually worked for me), I'd say it is designed to stuff up your Ubuntu system (hehe). I mean, my system is in such a bad state (ie fairly unusable) since the past week of Compiz updates, I seriously wouldn't mind getting rid of it. Problem is, when one tries to uninstall it, it wants to take ubuntu-desktop with it, which (correct me if I am wrong) isn't a good thing. So, is there any way to remove or at least totally disable Compiz without removing vital parts of Ubuntu with it? I really just want a working Gnome with Metacity doing its thing. You can read all the symptoms of my problem here:

[http://ubuntuforums.org/showthread.php?t=489206](http://ubuntuforums.org/showthread.php?t=489206)

---

### Post by tgm4883 on 2007-07-01
> **OzzyFrank said:**
> I've been trying to figure out what exactly Compiz does, and besides the wobbly windows (which disappeared when I installed Beryl) and desktop cube (that never actually worked for me), I'd say it is designed to stuff up your Ubuntu system (hehe). I mean, my system is in such a bad state (ie fairly unusable) since the past week of Compiz updates, I seriously wouldn't mind getting rid of it. Problem is, when one tries to uninstall it, it wants to take ubuntu-desktop with it, which (correct me if I am wrong) isn't a good thing. So, is there any way to remove or at least totally disable Compiz without removing vital parts of Ubuntu with it? I really just want a working Gnome with Metacity doing its thing. You can read all the symptoms of my problem here:

[http://ubuntuforums.org/showthread.php?t=489206](http://ubuntuforums.org/showthread.php?t=489206)

Your wrong, gnome-desktop is a meta package, it can be safely removed.  You may have problems if you try to do a distro upgrade without it, but you can reinstall it at that time.

---

### Post by OzzyFrank on 2007-07-01
OK, I admit I thought removing vast amounts of Gnome would render Ubuntu somewhat useless, since Ubuntu is built on Gnome. But what about the removal of "ubuntu-desktop" as opposed to "gnome-desktop"? Will I just end up with my Kubuntu desktop? If someone only had the one Ubuntu desktop, would it survive the removal of "ubuntu-desktop"?

---

### Post by tgm4883 on 2007-07-01
no, ubuntu-desktop is a metapackage.  Basically a list of other packages to install just by installing that package.

When you install ubuntu, everything in ubuntu-desktop gets installed, thats how it knows what to install.

---

### Post by OzzyFrank on 2007-07-01
So... what happens when you remove this metapackage which is basically a list of packages? Are you saying it will somehow know what to leave behind so the system is usable? I just want to make sure the answer isn't something like "You will end up with no Gnome but a perfectly usable command-line system", hehe!

---

### Post by Motoxrdude on 2007-07-01
Don't worry about it. It's not going to actually remove the ubuntu-desktop package. It just means that you will no longer have all the packages that come with ubuntu-desktop (compiz), but you will still have all your existing apps.

---

### Post by OzzyFrank on 2007-07-01
Yeah, figured my apps should all be cool, just wanted to make sure I have a desktop to launch them from, hehe (besides the Kubuntu desktop that seems to work). So basically removing "ubuntu-desktop" won't get rid of things Ubuntu needs, but will get rid of some of the extras like Compiz? Any control over what is removed? This will be a last resort, and am hoping either an Ubuntu update fixes this, or someone has an answer on how to fix Compiz, or at least disable it without having to remove it.

---

### Post by mcduck on 2007-07-02
> **OzzyFrank said:**
> Yeah, figured my apps should all be cool, just wanted to make sure I have a desktop to launch them from, hehe (besides the Kubuntu desktop that seems to work). So basically removing "ubuntu-desktop" won't get rid of things Ubuntu needs, but will get rid of some of the extras like Compiz? Any control over what is removed? This will be a last resort, and am hoping either an Ubuntu update fixes this, or someone has an answer on how to fix Compiz, or at least disable it without having to remove it.

Removing the ubuntu-desktop package will ONLY remove the ubuntu-desktop package, nothing else. Installing it will install every package that's in default Ubuntu setup.

If you remove a package that's in Ubuntu-desktop the ubuntu-desktop metapackage is removed, as all of it's dependencies are no more installed. (so if you remove compiz then compiz and ubuntu-desktop will be removed)

Removing the package is absolutely safe and will not break or change anything. The only thing is that if you want to upgrade to next Ubuntu version (instead of doing a clean install) you should reinstall ubuntu-desktop package before doing that to make sure you'll get all the new software in the new version.

---

### Post by OzzyFrank on 2007-07-02
Hey guys, thanks for all your info. Still trying to get my head around ubuntu-desktop installing everything you need but still being safe to remove, but at least I know if I ever needed to, it's safe to consider. But I've managed to get Gnome going with the boot options "noapictimer irqpoll", and not a mangled Gnome where I can't connect online. I must be a glutton for punishment as I am now currently updating Compiz again, hehe, but then I'm hoping that if the releases are so frequent at the moment, they are trying to rectify the problems so many are having. Once again thanks to all for your pearls of wisdom!

---

### Post by mcduck on 2007-07-02
Ubuntu-desktop package depends on all packages that are in default Ubuntu install. So when you install it, it tells your package manager that it needs Firefox, Gnome, OpenOffice and all the other things Ubuntu has by default. If you remove any of those packages, ubuntu-desktop's dependencies break so it's removed.

However, no other package depends on ubuntu-desktop, so when it's removed everyother package's dependencies are still satisfied. Nothing else needs to be removed.

In short way, ubuntu-desktop needs a bunch of packages, but no package needs ubuntu-desktop.

There are many other similar metapackages in Ubuntu's repositories, as they are usefull for installing groups of packages automatically, and also allow adding new packages to these groups (If developers update ubuntu-desktop and add some new program to it's dependencies, that program would get installed during a normal system update). You'll find at least metapackages for Ubuntu, Kubuntu and Xubuntu desktops, different kernels and so on. For example package linux-generic is a metapackage that has latest linux image, restricted modules etc. as it's dependencies, and having it installed makes sure you always have latest kernel and all related packages.

---

### Post by OzzyFrank on 2007-07-02
Aha, that makes a whole lot of sense now. A metapackage is basically like a list of packages, not an actual big package containing the other packages (which would make that a "megapackage", hehe?). And now I understand why one component being removed wants the ubuntu-desktop removed too.

So I suppose I should be asking whether it is safe to just totally remove Compiz, since people seem divided on whether it is really bound into the system, or just a window manager. I'm actually not going to remove it unkess things get worse, but it's good to know what people think. But as I said earlier, I can't even see what it does since I don't even have the wobbly windows anymore. I see there's a whole new control panel CompizConfig Settings Manager, with a whole bunch of effects checked, but I see no way to activate it. And I don't have Beryl running (so it shouldn't be interfering with Compiz), though installing that got rid of Compiz's wobbly windows, but can run Beryl with a script (I'm a sad ATI card owner).

Anyway, thanks for the info guys.

---

