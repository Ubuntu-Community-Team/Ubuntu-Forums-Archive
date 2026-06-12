---
title: "A Few questions about KDE"
date: 2009-07-27
forum: Desktop Environments
---

### Post by razorboy5 on 2009-07-27
going to officially install Kubuntu for my Laptop

was wondering about a few compatibility issues

are all the programs available to Ubuntu available for Kubuntu?
also is there like a synaptic manager for it? I used Kubuntu for a bit and didn't see anything like that

thx

---

### Post by 67GTA on 2009-07-27
All applications are Desktop environment independent. You can run Gnome apps in KDE and vice versa. You can install synaptic also. The only problem will be the themes. You can tell the GTK apps to use the KDE theme, but it is not perfect. Also any app ran as root like synaptic won't use the KDE theme.

---

### Post by Zorael on 2009-07-27
Sure, they use the same repositories. The only difference between "Ubuntu" and "Kubuntu" or "Xubuntu" (etc) is what packages come installed **per default**. The only exceptions are "remixes" which historically contain packages you can't get from the repos, of which Ubuntu Netbook Remix is nowadays a misnomer.

Kubuntu used to use the Adept Manager for package management, but the Adept suite as a whole was removed from the, again, default installation. It's still in the repositories even in Karmic, so you could install it if you wished, much like you could install Synaptic.

Nowadays there is no real "package manager" installed in the Kubuntu desktop package - only a normal "Add and Remove Software" graphical frontend; KPackageKit. It won't let you do advanced stuff like downgrading packages, but it will get stuff done for most users (installing, removing, upgrading).

So for the deeper stuff, grab Synaptic/Adept, or learn to love the terminal. If KPackageKit doesn't have its own icon, it should be in System Settings under Computer Administration. And unless you've set up policies to allow your user to install stuff in PolicyKit (System Settings -> Advanced tab -> PolicyKit Authorization), you may need to start it with superuser privileges. (**kdesudo kpackagekit**)


edit: To improve looks of apps when run as root;
> **oobuntoo said:**
> This problem has been around a long time. To get around it do the following.

For KDE 3.5.10 system do:

**sudo ln -s ~/.gtkrc-2.0-kde /root/.gtkrc-2.0**

For KDE 4 system do:

**sudo ln -s ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0**

Use 

**kdesudo systemsettings** 

to change themes for KDE apps that run under root privilege.

---

### Post by razorboy5 on 2009-07-27
hahaha Zoreal I love em Kookies

anyways thx for the replies will def try out Kubuntu now
knowing that it's practically the same thing really assured me on trying

thx

---

