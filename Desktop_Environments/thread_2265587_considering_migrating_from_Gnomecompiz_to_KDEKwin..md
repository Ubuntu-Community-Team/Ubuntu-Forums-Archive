---
title: "considering migrating from Gnome/compiz to KDE/Kwin. Opinions or advice?"
date: 2015-02-16
forum: Desktop Environments
---

### Post by wrjbarber on 2015-02-16
My preferred desktop has always been Gnome using Compiz so I can have the desktop cube and 3D windows on rotate. Since the release of Gnome 3, I have been using Gnome Fallback because Gnome 3 combined with Unity never seemed to get along with the Nvidia driver(s) on my machine. 

I currently have four problems with my setup:

1) Compiz Fusion Icon usually crashes on desktop loading. Which in turn means desktop wallpapers, skydome etc don't load until I go into CSSM and add new wallpapers to the list and set skydome to animate (which causes the compiz service to restart I think)

2) When using the latest Nvidia drivers, Flash objects on the web would sometimes cause the whole window to start flickering. Using the hotkeys to retract my desktop to cube and releasing it without flipping desktops. This happens regardless if I am using the latest available Adobe Flash or using the native Gnash. (in addition, Gnash would sometimes crash even when not viewing Flash objects at all, such as when browsing my documents folders) Rolling back to an older driver works, but at a noticeable performance hit

3) My boot partition is no longer big enough to accept updates. 

4) Despite much fiddling; I could never get Plymouth boot screens to work consistently. I tried using Super Boot Manager, which I suspect caused the lack of boot space in #3

There are numerous other fiddlin' little issues, mostly caused by my constant tweaking. I plan on buying an SSD this week and migrating over to that, making sure to create a bigger boot partition in the process. But since I am going to be basically doing the work of a fresh install, I am considering my options:

a) Go with the default Ubuntu/Unity install and then tweak/modify so that I get my beloved desktop cube and other tweaks back, like I have done every time before.

b) Roll my own Ubuntu/Gnome/Compiz oriented disk and migrate only my data to that fresh install. I have only ever compiled specific rescue disks before, but I don't see a problem rolling my own distro from scratch except for the problems inherent in keeping it updated...

c) Make the switch to Kubuntu or other KDE specific distro and install Kwin on that so I can get the KDE equivalents of desktop cube etc.

My goal is to  have a very polished looking, customized installation with a fair bit of eye-candy from boot to desktop.

Any advice, opinions, rants or flames all appreciated...

---

### Post by deadflowr on 2015-02-16
Wanna try out kde, or Kubuntu, then I say go for it.
Compiz doesn't seem like it'll be long of this earth, unfortunately.
And each release seems to either break or remove something...(slight rant)

That said, no need to install kwin if you install kubuntu, as it is already part of the default packaging (kde-window-manager)

Right now, though, if you were to move over to kde/Kubuntu, I would suggest installing 14.04.
I suggest this because, kde-world is prime to release the new plasma-desktop, version 5.
Which is still a little young.
If you installed a release such as 14.10, then in a few months you would need to upgrade to 15.04, and shortly there after move on to 15.10.
(Thems the breaks of a 9 month support cycle)

14.04 will still use plasma-desktop-4, so it's been around for a few years and is pretty stable, to me at least.
Also, since 14.04 is an LTS release, it'll be supported until 2019.
(Yes, Kubuntu gets 5 year LTS releases, just like Ubuntu)

Kubuntu/KDE is pretty customizable,.
So that end is not really a problem.
The real thing will be whether or not you feel comfortable using it.
Some love it, and some hate it.

My few cents.

---

### Post by Pumm4 on 2015-02-16
[COLOR=#000000]Interesting[/COLOR][COLOR=#000000]![/COLOR]

As deadflowr mentioned it is very important in terms of robustness & reliability to select 14.04 LTS.

KDE is an outstanding desktop environment, visually pleasing and has more point-and-click
 customization options and &#8220;eye candy&#8221; than any other GNU/Linux desktop. 


 ... but you might like something else for your specific situation ...


In short try Ubuntu MATE, here is why:

1) It uses forked Gnome 2 Desktop (tested and very reliable)
2) Lover RAM/CPU consumption in comparison to KDE & Unity
3) If you want to get things done & value your time
4) Green <3


The choice is Ultimately up to you. Good luck!

---

### Post by egeezer on 2015-02-16
If you want to live out the Last Great Days of Compiz (sad, but probably true) you could use a technique I learned from deadflowr a while ago:
Install Ubuntu 14.04 and immediately 
```
apt-get install xfce4 xfce4-goodies
```

This gives you an agile and highly customisable Xfce desktop, and you have access to all the Compiz stuff from Ubuntu.  
The only downside I've found is that LibO pages take a few seconds (5 or so) to open fully, though they are writable even before that.

But hey, you get The Cube! The Sphere! The Magic Lamp! (No Explode, sadly)  Might be worth a try.

---

### Post by wrjbarber on 2015-02-19
Thanks for the feedback guys.

@Deadflowr For what it's worth, I plan on sticking with LTS releases or the equivalent as much as possible. I have to admit that my Gnome vs KDE preferences formed way back in the Breezy Badger days. I installed Ubuntu and deliberately installed both DE/Window managers on my system. I logged into one or the other on an alternate basis for a few weeks and found that I had gravitated to the Gnome set up. (mainly because, coming from the Windows world, I found the Gnome equivalents of Control Panel, Device Manager and Display Properties an easier learning curve for me) That was obviously a while ago, which is one of the reasons I am willing to give the KDE option a shot. I'm more versed in how Linux works now, so changing to KDEwon't be as much as a challenge as it once seemed.

@ Pumm4 Thanks for mentioning MATE. I already had Linux Mint on my short list of possible distros to investigate as an alternative to the options I listed above. I just thought asking the Ubuntu forum for advice on possibly switching to Mint to be, well, kinda rude (smile) So in my post I focused on the Ubuntu based options.

@ egeezer Thanks for reminding me about XFCE. I had only ever used it as a super light recovery and LiveCD desktop, so I had never looked into its customizing potential. I mentally pigeon holed it there and never reconsidered it. But I will know.

For every one else: A friend suggested something that seemed so obvious I wanted to hit myself for not thinking of it first. She said why not hit youtube for videos showing people doing the default installs of the combinations I am considering and then look at videos of desktops people have done cool customization to. I've been dealing with a LOT of medical stuff this week, so I haven't gotten to that yet. I plan on binge watching youtube over the weekend. I'll keep this thread updated for the benefit of others.

---

### Post by kerry_s on 2015-02-19
you don't have to switch to mint to get mate desktop, there's a official ubuntu version.
[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

---

