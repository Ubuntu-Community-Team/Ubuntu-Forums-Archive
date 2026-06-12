---
title: "KDE or Kubuntu?"
date: 2010-03-17
forum: Desktop Environments
---

### Post by Randymanme on 2010-03-17
I notice in synaptic package manager at lot of KDE packages; e.g., KDE base,  KDE minimal, KDE standard, KDE full, et al.  But, then, on top of all that, the Kubuntu Desktop System.

I'm curious as to how a KDE desktop environment on Ubuntu would differ from the Kubuntu desktop system?

I'm particularly interested in having Konqueror installed without having to put up with the bloat of all the other KDE packages that it drags with it.  I note that synaptic's description of the Kubuntu desktop system says that that package can be removed if one does not want all the packages.  May I presume that that means that I can install Kubuntu and then get rid of everything else other than Konqueror and K3b (and minimal dependencies)?

---

### Post by 3Miro on 2010-03-17
You can either install Kubuntu and get KDE only or you can install Ubuntu and then get kubuntu-desktop from the repos so that you have KDE and Gnome installed. For me, the second way was better. I currently have KDE, Gnome and XFCE installed and I am using all of them.

To install KDE
```
sudo apt-get install kubuntu-desktop

``` to install XFCE
```

sudo apt-get install xfce4
```

If all that you want is konqueror, you should be able to install that without the need for the entire environment. You will have to add some QT and KDE packages, but not too many. Look for konqueror in the synaptic package manager.

---

### Post by Zorael on 2010-03-17
**kubuntu-desktop** is a package bundle with a typical KDE software compilation as well as some default settings. So if you install **kubuntu-desktop**, you will get the standard Plasma desktop shell along with other standard KDE apps, from file managers (Dolphin, Konqueror) to web browsers (Konqueror) to instant messengers (Kopete) to IRC clients (Quassel). This also includes the login manager (kdm) and boot/shutdown theme (usplash), so essentially your installation will carry the Kubuntu brand and look like a Kubuntu distro.

This is where people cry bloat when they install **kubuntu-desktop** to "try KDE" out on their existing Ubuntu GNOME installation, as they really only want to get the Plasma desktop shell (and perhaps core apps like Dolphin). If you only want to try the look and feel of KDE but still want to use your current apps, grab **kde-minimal**.

Beware, though, that chances are your GTK apps will look like dirt. **kubuntu-default-settings** has a GTK theming file that makes them look much better, but you're opting out of it. And your sound will probably be muted or at 0% until you open up the volume mixer (KMix) and raise those sliders. (PulseAudio mutes them and imposes its own, but Kubuntu doesn't use Pulse.)

Really, to stop confusion they should rename the current Ubuntu to "Ubuntu GNOME", make Kubuntu be synonymous to "Ubuntu KDE", and rename the base repositories to "Ubuntu Core". As it is now, if you run Ubuntu (GNOME) and you install KDE packages, when exactly does your computer stop running Ubuntu (GNOME) and start running Kubuntu? What if you have two full-fledged installations next to eachother? Is it still Ubuntu (GNOME) despite all those KDE apps? Or is it Kubuntu with GTK apps? And what of a minimal, headless machine with only terminal apps; is it still "Ubuntu", with GNOME and GTK apps being implied?

---

