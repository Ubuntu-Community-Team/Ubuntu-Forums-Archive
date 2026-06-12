---
title: "xubuntu with kde components"
date: 2020-09-01
forum: Desktop Environments
---

### Post by Solour on 2020-09-01
Hi,

I would like to know whether I can mix xubuntu with e.g. kubuntu.
For example, is it possible to install kate in xubuntu?

Best

---

### Post by CatKiller on 2020-09-01
It's fine to do that.

However, applications rely on a bunch of support libraries to function. If all your applications are using the same libraries - because they're all GTK applications, or because they're all KDE applications - then you only need one set of libraries on disc, or in RAM. If you mix-and-match, though, then you need both sets on disc and both sets in RAM. So you'll find that you need to download more, and have higher RAM usage, than you'd expect from just changing your text editor.

All the new KDE components will share those KDE libraries, though, so resource usage won't keep going up as you add more.

On a powerful machine you probably won't even notice it, but if it's already marginal that might make a difference.

---

### Post by Solour on 2020-09-01
Ok, this is already good to know.

Another related question:
Is it possible (and how) to change between ubuntu/kubuntu/xubuntu?

---

### Post by CatKiller on 2020-09-01
> **Solour said:**
> Is it possible (and how) to change between ubuntu/kubuntu/xubuntu?

It's *possible*, and pretty straightforward, but it's a pain.

First, the good news: you just install the meta-package - ubuntu-desktop, kubuntu-desktop, xubuntu-desktop, or whatever - and it pulls in everything you need. Log out, and then you can pick whichever desktop environment you want to log into from the login screen. Easy peasy.

However, the bad news. Each desktop environment comes with a full suite of software. Text editor, file browser, settings application, media player, what-have-you. That's exactly what you want if you're using a desktop environment. But if you have *two* desktop environments then you now have two text editors, two file browsers, two settings applications, two media players, and two what-have-yous, all showing up in your menus and making things untidy. Three, and you get three sets of everything. And uninstalling the meta-packages *doesn't* generally remove all of the things that got pulled in.

VMs or live USBs are the best way of testing out the different desktop environments, rather than installing new ones over the top. Then you can pick the one that you like most to actually install.

---

### Post by ajgreeny on 2020-09-01
> Another related question:
Is it possible (and how) to change between ubuntu/kubuntu/xubuntu? 
You can install other metapackages for the full desktop environments, eg ubuntu-desktop, kubuntu-desktop, etc, and then chose what you want to use at the login screen, but generally it is much better not to do so because it is possible that the configurations in your home get confused and cause problems; it may not be likely but it can happen.
It may also confuse you as you'll have duplicate applications for the text-editor, file-manager, terminal, etc.

I always install a few applications from the KDE section of the repos, digikam, kmymoney, because I have never found any GTK applications that work as well as them; it means that I have to also accept the installation of many qt lib files in order to run those applications.  I am happy to do this but I would never add a full alternative DE though others do it happily without any problems.

Your choice; I just tell you the potential problems.

EDIT:
Beaten to it by CatKiller, but at least we both told you the same story.

---

### Post by Dennis N on 2020-09-01
If the application is available in a Flatpak, that is another choice - one that I prefer as the support libraries for KDE are installed as a single bundle (called a runtime) that is easy to remove. It happens that **kate** is available in a Flatpak. Visit [Flathub]("https://flathub.org/home") website for information on setting up Flatpak support, and to find Flatpaks to install.

---

### Post by geofftf on 2020-09-07
I have ShowFoto (DigiKam without the database functions) installed on Xubuntu 20.04. ShowFoto pulled in 600 MB of dependencies when it installed. On a fresh boot, my memory used just showed as 435 MB with 3.0 GB available. After launching ShowFoto the memory used showed as 451 MB with 3.0 GB available.

My processor is a third generation i3 and everything is fast. This computer cost the local equivalent of about $40 from eBay, including postage. You do not need to worry.

---

