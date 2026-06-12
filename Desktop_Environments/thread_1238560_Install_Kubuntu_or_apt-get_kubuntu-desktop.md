---
title: "Install Kubuntu or apt-get kubuntu-desktop ?"
date: 2009-08-12
forum: Desktop Environments
---

### Post by Findarato on 2009-08-12
Hello there,

I am a 2 year user of ubuntu soon (my ubuntu-bday is somewhere around october :P) and have wanted to try out KDE for some time now. Even though I know Kubuntu isn't the best KDE implimentation, it will get me started on KDE while keeping me in ubuntu and, more importantly, the apt-get .deb environnement :). 
My question now is : should I go on and simply install kubuntu-desktop on top of my current ubuntu installation (running gnome), or would I be better off making a backup of my important files and reinstalling a new and clean kubuntu ?

Thank you very much for your help and your insights

---

### Post by Raboch on 2009-08-12
Well, installing Kubuntu-Desktop on your existing install has the advantage of being much quicker to set up than backing up all your files and installing from a Kubuntu CD and so on. And if you don't like Kubuntu you could [go back]("http://psychocats.net/ubuntu/puregnome") to gnome only easily.

I started out with Ubuntu and installed Kubuntu-Desktop to get a feel for KDE while having something familiar to fall back on.

But Kubuntu-Desktop by default installs KDE 4.2 instead of KDE 4.3 which is the new stable version and which some users have installed. 4.3 seems to be a bit less buggy and provide slightly better features, but on the other hand installing 4.3 on Kubuntu isn't supported officially yet so it might be better to stick with 4.2 for now.

---

### Post by ugm6hr on 2009-08-12
Maybe just install kde rather than kubuntu-desktop?

I don't use kde, but much preferred my Xfce to be homegrown than xubuntu-based.

[http://packages.ubuntu.com/jaunty/kde](http://packages.ubuntu.com/jaunty/kde)

---

### Post by aysiu on 2009-08-12
I would just run the live CD of Kubuntu if you have 256 to 512 MB of RAM.

If you have 1 GB of RAM or more, you can install Kubuntu as a virtual machine (using VirtualBox) inside Ubuntu to see how you like it.

Once you've decided you like it (if you do), you'll have a better sense of whether you'd rather run it side by side with Ubuntu or replace Ubuntu completely with Kubuntu.

---

### Post by jauntyjackalope on 2009-08-12
I would install kubuntu-desktop if you are just wanting to try it. It will be less of a hassle. Or you can just switch to xfce :) its pretty amazing and way faster!

---

### Post by oldfred on 2009-08-12
I have Ubuntu that I have upgraded many times and installed a few k applications. I decided to install kubuntu-desktop to my ubuntu just to try it and it allowed me to choose which to load when I logged in.  
I then decided I did not want it and could not uninstall as it would also remove all my k apps that I wanted to keep. I unstalled kde and left everything else.

---

### Post by Findarato on 2009-08-12
Is there actually any difference between the two approaches (in terms of speed, etc.) ? If so, which are they ?

---

### Post by Findarato on 2009-08-16
Bump & would installing Kubuntu-Desktop cause me any problems ? Will my computer be any slower and, if I choose to remove it later, will it do so without any problems ?

---

### Post by aysiu on 2009-08-16
It won't cause any *major* problems, but there may be minor annoyances.

For example, Kubuntu puts a small .desktop file on the desktop. In KDE, that .desktop file actually serves a function. In Gnome, it just appears as a useless file.

Kubuntu may also change your boot splash theme.

And your menus may be cluttered up by having a combination of both Gnome-native and KDE-native applications.

If you want to be sure you remove everything, when you install Kubuntu, make a copy of all of the packages to be installed and put those in a text document. Then when you to remove it, type ```
sudo apt-get remove --purge
``` and paste the package list back.

---

### Post by crpenaherrera on 2009-08-27
Hello every one,

I'm a new linux-kubuntu user. I would like your help in an issue. I was uninstalling Cairo dock with the KpackageKit and I unistall all the kubuntu desktop by mistake. From other post I read that it happens if sometimes while using the interface instead of the terminal. So, if I try to install using apt-get kubuntu desktop will help me in recover all kubuntu functionality or should I installed all from the cd again? 

Thanks for the help in advance....

---

