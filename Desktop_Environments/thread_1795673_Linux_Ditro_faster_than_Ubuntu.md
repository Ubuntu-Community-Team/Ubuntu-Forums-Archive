---
title: "Linux Ditro faster than Ubuntu"
date: 2011-07-03
forum: Desktop Environments
---

### Post by chuchi on 2011-07-03
Hi friends!! I am an Ubuntu user and I have an old computer. My problem is that when I am watching movies, the movie reproduces with difficult, choked, faltering, and it doesn't happen in Windows. 

I don't know what the problem is. If it is a problem with codecs, Could you recommend me good codecs?? 

But if it is a problem with the distro. What is, in your opinion, the faster Linux Distro? So I can play movies without stops?

Thank you very much!!

---

### Post by nzjethro on 2011-07-03
Hi chuchi.

1) Make sure any unneeded programmes are turned off. Programmes such as compiz, transmission, and brosers running in the background can consume a lot of your computer's resources, and make video viewing choppy. Also, you should turn off Desktop Effects (in the Appearances menu), as these can severely slow down a computer.

2) While a full on distribution change may not be necessary, if you want snappier performance from lower specs, consider one of the lightweight *ubuntu releases. Both Xubuntu (which uses Xfce instead of Gnome), and Lubuntu (which uses LXDE) are more lightweight, and thus run better on computers with less RAM or a slower CPU. If you're feeling technical, the *box window managers (like Fluxbox, Blackbox) are even more lightweight, but this can take some technical expertise.

3) If you like Ubuntu, and you want to go real lightweight, consider doing a minimal install, then installing Xfce or LXDE (or one of the *boxes) overtop. A minimal install installs just the barebones packages needed to run your Ubuntu machine, meaning that computer resource usage is reduced further. Again, this is semi technical.

4) If you want a full Distro change to get lightweight as, check out Puppy Linux. It's designed to use as little resources as possible (it can be installed only in your RAM!), meaning performance is improved. Mind you, a full on distro change may be a bit extreme just to enhance your video playback! ;)

My advice, start with 1, if that doesn't work to your liking consider 2, and so on. With the technical options (2-4), if you are a bit daunted by the process, post back and someone here will be able to run you through the what the decision involves, and guide you through it if you want to take the plunge.

---

### Post by chuchi on 2011-07-03
Hi nzjethro!! thank you very much for your post!! I tried your first one, and it didn't work. That's why I would install another Distro with Ubuntu (thanks to Grub, I won't uninstall Ubuntu). 

I have searched in the Web and find that Slackware, Arch and Gentoo are the fastest Distros. Which one you recommend me? 
Thank you very much!

---

### Post by chuchi on 2011-07-03
I have an CD of Wifiway, but I use it only for a live CD. I know you can install it on the hard disk. Is it a good Distro??

I wonder this problem. In Windows I can see movies without problems. And as we all know, Ubuntu is much faster than Windows (much much!!). So why I have problems in Ubuntu?

---

### Post by nzjethro on 2011-07-03
> **chuchi said:**
> 
I have searched in the Web and find that Slackware, Arch and Gentoo are the fastest Distros. Which one you recommend me? 


I'll admit, I haven't tried any Linux distro other than Ubuntu, so this is based on my knowledge of others' experiences.
Gentoo is a distribution that you have to compile yourself, and thus (theoretically at least) should be the fastest of the bunch. But at the same time, because you have to compile it, I've heard it can be a real PITA - a lot more hard work than Ubuntu. I'm not sure what the community and level of support for Gentoo is like, but it's less widely used than Arch, so there may not be the same level of support (which isn't ideal seeing as how you'd probably need the most support of all for Gentoo).

Arch and Slackware, on the other hand, get their speed from just being minimal installs, which means that as you install more programmes, you're going to lose speed. I have heard a lot of good things about Arch, and in fact I think Arch will be my next step when I have a bit more experience with Linux in general. Arch is also pretty widely distributed, so there's a lot of support.
Slackware, I'm sorry, I've had no experience with, so I cannot comment.

What I would suggest, if you're undecided between them, is to create small (10GB or so) partitions, and install the distros you are interested in. Use each one for a week or two, and see which one suits your needs best. Also, read some comments on here in the Other Distros/OS Forum, and see what others are saying about Gentoo/Arch/Slackware. I hope you find one that suits you. :)

---

### Post by nzjethro on 2011-07-03
> **chuchi said:**
> 
I wonder this problem. In Windows I can see movies without problems. And as we all know, Ubuntu is much faster than Windows (much much!!). So why I have problems in Ubuntu?

As for this, do you have all of your drivers fully optimised for your system? What media player are you using?

---

### Post by chuchi on 2011-07-03
Hi nzjethro!! thank you! I don't know if i have all the drivers  fully optimised, I don't know how to do it. I use VLC.

---

### Post by nzjethro on 2011-07-03
To check if your drivers are optimised, go to System > Administration > Additional Drivers (or something similar, depending on your release). It should have a list of drivers (perhaps just one), and you want to make sure that each one is set to "Enabled".

As for choppy playback with VLC, check out [this thread.]("http://ubuntuforums.org/showthread.php?t=569136") It has a number of solutions to help with VLC playback, which may help your situation.

---

### Post by chuchi on 2011-07-03
**When I go to ** System > Administration > Additional Drivers it throws "**No proprietary drivers are in use on this system", what does it mean?**

---

### Post by mikejonesey on 2011-07-03
iv'e used at  least 8 distros, debian being my primary, but i wouldn switch just for speed, you can configure any breed as you wish, to free up cpu n ram for video playback stop processes running that you don't use like wireless, bluettoth, apache, any databases...

ls /etc/init.d/

for example on my lappy i have postgres which i don't need unless i'm doing some stupp for work so i switched the run levels to 345 (i have to manually start it with /etc/ini.d/postgresql star now)

the enviroment you use will effect your cpu n ram so if u want to watch a film switch to meta city (metacity --replace &)...

finally if u have a cruddy dvd drive maybee copy to harddrive n play from there...

---

### Post by oldos2er on 2011-07-03
> **chuchi said:**
>  I have an old computer.

What are your hardware specs?

---

### Post by jvgeli on 2011-07-08
How old is "old." If it is old enough not to support effects and you might have it turned on thats one thing. Also, you might be using drivers that are not optimized for your hardware, GPU.

---

