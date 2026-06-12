---
title: "How to remove and re-install all X graphical desktops"
date: 2012-11-17
forum: Desktop Environments
---

### Post by bonesTdog on 2012-11-17
Hi all,
I am an intermediate user, which means I know just enough to get myself  into trouble... I have borked my Ubuntu 12.04 graphics environment  somehow playing with Virtualbox. I can boot into text mode and  everything works fine, but startx fails to start correctly and it won't  boot at all in graphics mode. I have a lot of customization, so I am  trying to avoid re-installing the OS and hoping to remove all GUI [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important]desktop[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#")  environments and re-install from scratch in hopes that takes care of my  problem. I have tried to do that, but need a lifeline. I have run apt-get purge for the following  programs:
xorg, unity, unity-common, gdm (I had Gnome 3 installed).
 
Now when I run startx, it still loads a portion of the desktop so obviously I have not removed everything to strip it all the way down to text only.
 
Any words of wisdom from one of you gurus?

---

### Post by DuckHook on 2012-11-17
Removing Unity seems to be inherently difficult. Here are some threads with supposed solutions.

[http://blogs.operationaldynamics.com/paul/opensource/not-unified-removing-unity-from-ubuntu-12-04-lts](http://blogs.operationaldynamics.com/paul/opensource/not-unified-removing-unity-from-ubuntu-12-04-lts)
[https://plus.google.com/105745543515055969267/posts/H6wkF9CF7Dr](https://plus.google.com/105745543515055969267/posts/H6wkF9CF7Dr)

I've never tried any of them, so you're on your own in the risk department. It may also be a one-way street, with no way to easily reinstall Unity withour some key or config files missing. The first link is especially useful as it contains warnings against removal of files that the window manager requires for any alternate desktop to remain functional. Again, pure conjecture, as it is not a well documented process.

In a way, the difficulty is understandable. A DE is so fundamentally integrated to any distro that one can see why it would be difficult to lobotomize it. You may be better off just backing up your important stuff and reinstalling. You will probably spend less time recustomizing than you will trying to fine tune a lobotomy.

---

### Post by bonesTdog on 2012-11-24
Thanks for the direction. I discovered what caused my original problem... A stupid mistake! I ran out of space on my partition. Once I enlarged the partition I was able to re-install all the removed programs and all is now good.

One exception - I now can't install a working version of VirtualBox any longer. As you suggested, I think I may re-install from scratch rather than continue to try to "revive my lobotomy"!

Funny how simple it is to install a desktop environment from scratch, yet so difficult to remove it completely. Hrmph.

---

