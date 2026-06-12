---
title: "Ubuntu Gnome + Cinnamon DE"
date: 2015-03-09
forum: Desktop Environments
---

### Post by eipapp on 2015-03-09
I'm currently running Ubuntu 14.04 LTS along with Gnome 3.10 shell and Cinnamon DE on my desktop computer.
I find that for the most part and only use Gnome DE and Cinnamon DE and rarely Unity.
My question is, can I just load the Ubuntu Gnome desktop and then add the Cinnamon DE to it, thereby, bypassing Unity install altogether ?
Or, do I need Unity for the other two to work properly. Just wondering.........
Any help would be greatly appreciated. 

Thanks much,
Bruce

---

### Post by raptir on 2015-03-09
> **eipapp said:**
> I'm currently running Ubuntu 14.04 LTS along with Gnome 3.10 shell and Cinnamon DE on my desktop computer.
I find that for the most part and only use Gnome DE and Cinnamon DE and rarely Unity.
My question is, can I just load the Ubuntu Gnome desktop and then add the Cinnamon DE to it, thereby, bypassing Unity install altogether ?
Or, do I need Unity for the other two to work properly. Just wondering.........
Any help would be greatly appreciated. 

Thanks much,
Bruce

There would be no need to have Unity installed, but you may end up with different pre-installed applications depending on your initial install process. If you want to have both GNOME and Cinnamon installed, the Ubuntu-GNOME image would be a good place to start.

If you wanted just Cinnamon, you could start from an Ubuntu minimal image and use tasksel/aptitude to install Cinnamon.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by grahammechanical on 2015-03-09
We can install Ubuntu Gnome ISO image which comes with Gnome 3 shell and then install Cinnamon DE on it because Ubuntu Gnome uses the same software centre as Ubuntu. 

But I suggest that removing Unity from Ubuntu would be more complicated then just leaving it there and not using it. I say this because I do not think that Ubuntu is crafted to have a swap out and swap in user interface. Otherwise we would not have different flavours of Ubuntu as distributions in their own right but just alternative user interfaces on the same basic OS.

Regards.

---

### Post by eipapp on 2015-03-09
To install Gnome I would download the Ubuntu Gnome Desktop as opposed to Gnome-Shell which I have now ?
Once installed and running, I could then add the Cinnamon DE on top of that same as I did with Unity using a PPA ?

---

### Post by tgalati4 on 2015-03-09
There is a reason why Linux Mint is number 1 (at least right now) on [http://distrowatch.org](http://distrowatch.org).  It has a decent, working-out-of-the-box Cinnamon or MATE desktop.  It would be nice to have a big icon on the Unity desktop  that says "Remove Unity and Install Something Else" but that does not exist.  So you can try to remove Unity and expect breakage or load another flavor of Ubuntu or another Linux distro such as Linux Mint.  You have a choice.

---

### Post by buzzingrobot on 2015-03-09
A number of applications in the Ubuntu repositories are built with dependencies on a few Unity packages, to ensure they leverage Unity correctly. When those applications are installed, those libraries will be pulled in as dependencies (even on Mint) even if Unity is not the environment in use. (The reverse happens, for example, if you want to install Mint-specific packages on Unity.)

While it is possible to carefully and laboriously remove many -- but not all -- Unity packages, as mentioned upthread, it really isn't worth the trouble. When a desktop environment is selected at login, any other DE's installed on the system are not executed. If an application requires a dependent package from Unity or any other DE, that package must be available when that application is executed, regardless of the DE in use.

---

### Post by eipapp on 2015-03-09
I guess I was thinking about a complete fresh install of Ubuntu Gnome then adding Cinnamon after. In the end, maybe it's best to just leave things as they are. I've used Mint in the past but I guess I'm a sucker for Ubuntu as that was my first introduction to Linux and I feel a certain affinity to it.

---

