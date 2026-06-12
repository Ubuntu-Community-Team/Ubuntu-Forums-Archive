---
title: "What r consequences of running KDE apps in Ubuntu (Unity)?"
date: 2016-12-28
forum: Desktop Environments
---

### Post by ScientificProp on 2016-12-28
I've wondered about this question several times in the past few years. For example, what consequences are there if I run Dolphin (or GwenView), both are designed for KDE and are provided in Kubuntu, on the standard Ubuntu with the Unity desktop? For example, does it need to load KDE code and is therefore less efficient than running an application that is designed for Unity. Conversely, are there similar consequences when running an application designed for Ubuntu in a KDE desktop environment (Kubuntu)? It's been difficult to find the program / application with the set of features that I'm looking for. It is often said that Linux can be customized, so I'd like to better understand the downside of that customization. (you know, you don't get something for nothing!).
Thnaks for your thoughts.

---

### Post by SeijiSensei on 2016-12-28
Installing a KDE program will bring in a lot of additional libraries because KDE relies on a different toolset (Qt).  That said, on any reasonably modern computer you'll have sufficient disk space to store those libraries, and performance should be on a par with running a fully KDE system like Kubuntu.  

The reverse holds true as well.  Kubuntu does a fine job of displaying GTK applications that run natively on GNOME/Unity and offers the ability to tweak their appearance in its System Settings.  Firefox and Thunderbird run just fine on Kubuntu.

Just try installing Dolphin from the terminal with "sudo apt-get install dolphin" and you'll see what else is needed.  Once the basic libraries are there, adding other KDE programs won't have the same overhead.

Another option is to run Kubuntu in a VirtualBox virtual machine on top of Unity.  You can make the two installations share the desktop with "seamless mode."  I think that's overkill though.

---

### Post by vasa1 on 2016-12-28
I don't use Ubuntu (Unity), but, from what I recall, it used to have quite a few Qt-based components. I think the "cost", on a relatively modern machine, will be negligible: some disk space to accommodate dependencies, mainly when you install the first KDE app, and some RAM.

Again, I'm just speculating here, but one caution maybe to avoid installing KDE software that would provide you with an entire KDE login session (and KDE desktop). At that point, there could be some amount of tussle.

As SeijiSensei suggests, take a look at what the system proposes to add in addition to the package you want before accepting the proposal.

You could also use a simulation (which won't need *sudo*):```
apt-get install -s okular
```where okular is an example of a very competent PDF file viewer.

You could also compare what's proposed with and without the *--no-install-recommends* option. I've gotten away with installing many packages using the *--no-install-recommends* option.

If you have doubts, start a new thread for a specific issue with a descriptive title.

---

### Post by Keith_Helms on 2016-12-29
I run Xubuntu and install whatever apps I like without worrying if they originated in Ubuntu, Kubuntu or Timbuktu.  For example, I use the K3b disc burner application and when I install it it pulls in a bunch of KDE support libraries.  Does that hurt anything or impact my system other than using a little extra drive space?  Not that I've noticed.

---

### Post by ScientificProp on 2016-12-31
Thank all, for the good information. You all verified about what I expected, and hoped. I'm building a system from old and new parts and so I've plenty of hard disk space. I've already run Dolphin, with no noticable negative consequence. I was also hoping to understand why some applications are not listed in the Ubuntu Software Installer, but there known to be available for other Linux distributions.
Thanks again for the help.

---

### Post by SeijiSensei on 2017-01-01
Care to give us examples of such applications?

---

