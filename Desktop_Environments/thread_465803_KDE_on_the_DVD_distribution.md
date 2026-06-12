---
title: "KDE on the DVD distribution?"
date: 2007-06-06
forum: Desktop Environments
---

### Post by amire80 on 2007-06-06
Hi,

Is KDE included on the Ubuntu DVD?

And if it is included, then what's the difference betweenm then what is the difference between the Kubuntu DVD and the Ubuntu DVD? Is it just that KDE is the default on Kubuntu?

---

### Post by Nythain on 2007-06-06
i dont think kde is available on the disk for any ubuntu release, thus kubuntu... but it IS available via the repositories and apt-get

sudo apt-get install kde-core
for the bare minimum

sudo apt-get install kdebase
for a little bit more

sudo apt-get install kubuntu-desktop
for the complete kubuntu distro

difference between ubuntu and kubuntu is the desktop environment (gnome vs. kde). There are tons of really log debates and discussions already available in these forums on this topic

other difference is prepackaged and default installed software... since ubuntu uses gnome it comes with gnome/gtk specific software, and kde relies more on kde/qt software, though either software will run on both DE's.

my advice is figure out wich one you like better, gnome or kde, then install the version of *buntu that fits, installing any additional software via adept/synaptic/apt-get that you would require.

example, i prefer kde over gnome so i start off with a kubuntu install. next i install certain software i cant live without (firefox and synaptic to name a few)... then i remove any unwanted software (wich isnt much) that kubuntu installed default and i have my perfect for me set up...

others go the other route, and install ubuntu, followed by certain qt/kde apps like k3b, amarok, kopete, etc...

wichever works for you

---

