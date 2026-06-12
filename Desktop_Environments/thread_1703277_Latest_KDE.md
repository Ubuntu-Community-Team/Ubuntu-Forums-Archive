---
title: "Latest KDE"
date: 2011-03-09
forum: Desktop Environments
---

### Post by Jonny87 on 2011-03-09
Does the Maverick repositories have the latest release of KDE 4.5? I want to install it into my Ubuntu 10:10 install. If not does any one know how I might go about getting it (the most stable way possible)?

---

### Post by ankspo71 on 2011-03-09
Hi,
Maverick's repositories have KDE version 4.5.1, but there is an upgrade to 4.6.1 if you add an extra repository. Here is the KDE 4.6.1 news announcement at Kubuntu's homepage: [http://www.kubuntu.org/news/kde-sc-4.6.1](http://www.kubuntu.org/news/kde-sc-4.6.1) . 

To install KDE 4.5.1, all you need to do is install the package called "kubuntu-desktop". You can skip this step if you want to install KDE 4.6.1 though.

For KDE 4.6.1...You can add the extra repository in Synaptic Package Manager by opening up Synaptic Package Manager, then go to the menu, Settings > Repositories > Other Software (tab) > Click on the Add button, then paste the following code in the "APT Line:" box:
```
ppa:kubuntu-ppa/backports
```
Now press "Add Source"
Now you will be alerted to reload the repositories, so do that by clicking on the reload button at the top of Synaptic Package Manager.

Now you can install the updated version of "kubuntu-desktop" which includes KDE 4.6.1.

I think you can do all this using Software Center too.

---

### Post by Jonny87 on 2011-03-10
> **ankspo71 said:**
> Hi,
Maverick's repositories have KDE version 4.5.1, but there is an upgrade to 4.6.1 if you add an extra repository. Here is the KDE 4.6.1 news announcement at Kubuntu's homepage: [http://www.kubuntu.org/news/kde-sc-4.6.1](http://www.kubuntu.org/news/kde-sc-4.6.1) . 

To install KDE 4.5.1, all you need to do is install the package called "kubuntu-desktop". You can skip this step if you want to install KDE 4.6.1 though.

For KDE 4.6.1...You can add the extra repository in Synaptic Package Manager by opening up Synaptic Package Manager, then go to the menu, Settings > Repositories > Other Software (tab) > Click on the Add button, then paste the following code in the "APT Line:" box:
```
ppa:kubuntu-ppa/backports
```Now press "Add Source"
Now you will be alerted to reload the repositories, so do that by clicking on the reload button at the top of Synaptic Package Manager.

Now you can install the updated version of "kubuntu-desktop" which includes KDE 4.6.1.

I think you can do all this using Software Center too.

Thanks for your response, just wondering, is KDE 4.6.1 stable? I want something stable.

---

### Post by PaulW2U on 2011-03-10
> **Jonny87 said:**
> just wondering, is KDE 4.6.1 stable? I want something stable.
I'm finding KDE 4.61 is very much improved over every version I've used in the past both in looks and stability. I'm finding a couple of really annoying bugs but they may be related to my test version of Kubuntu 11.04.

I would say go ahead and install the upgrade.

---

### Post by ankspo71 on 2011-03-10
Hi,
I agree with the above poster. I find KDE 4.6.1 to be better than KDE 4.5.1 in terms of stability and appearance.

The only unstable issue that I have personally noticed is when I was importing and removing multiple color schemes and qtcurve themes in System Settings which triggered the desktop to crash and log me out. It's happened to me twice already, but it hasn't stopped me from accomplishing what I was trying to accomplish. I haven't found any other desktop related crashes or anything else I would consider unstable though.

---

### Post by SeijiSensei on 2011-03-10
I upgraded an older laptop (Inspiron 640m) running 10.10 to KDE 4.6.1 the other day.  It puts considerably greater demands on the system's video resources which that machine's motherboard Intel graphics couldn't handle.  I found I had to turn off desktop effects in order to scroll smoothly in Firefox.  I'll still be upgrading my desktop machine which has a quad-core and NVIDIA 9500 GT graphics.

10.10 with KDE 4.5 worked fine on the laptop before upgrading.

---

