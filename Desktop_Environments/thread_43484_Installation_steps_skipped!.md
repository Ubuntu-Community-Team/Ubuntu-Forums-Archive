---
title: "Installation steps skipped!"
date: 2005-06-22
forum: Desktop Environments
---

### Post by smilelover on 2005-06-22
Hi guys,
i have tried to install kubuntu 3 or 4 times and I have always encountered the following problem:

The last screen I've seen when installing was [this](http://shots.osdir.com/slideshows/306/26.gif). Kubuntu never showed me [the xorg config. screen](http://shots.osdir.com/slideshows/306/27.gif)  and always launched xorg right away. When starting X, my monitor always cried that the desired mode is out of range (some insane frequencies...i don't remember) I had to reset X (Ctrl+Atl+Bckspc) in order to see KDM...

when installing it just gave me the command line and told me I can enter "exit" in order to get back to some setup program or so... and "exit" did nothing. just wrote logout and returned back to the shell. this happened right after the "configuring..." process.

is this caused by UFO or what? :)

(I have Radeon 9550)

---

### Post by shakin on 2005-06-22
I'm not sure about the install problems, but try running 'sudo dpkg-reconfigure xserver-xorg' and see if that lets you setup your video properties.

You can also try installing ubuntu then running 'sudo apt-get install kubuntu-desktop' to get the kubuntu system. Your problem might have something to do with the kubuntu cd.

---

