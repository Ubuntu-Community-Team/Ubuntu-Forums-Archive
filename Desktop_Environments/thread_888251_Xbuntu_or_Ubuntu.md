---
title: "Xbuntu or Ubuntu ?"
date: 2008-08-12
forum: Desktop Environments
---

### Post by Dreamerman on 2008-08-12
Hi. I've installed Ubuntu on my fastest machine (only a P4 1.8Mhz 1G ram) & think it runs better & faster than XPpro. I am wondering if I should install Xubuntu instead. 

I hear that Xubuntu is lighter on resources compared to Ubuntu so technically I should get better performance. But I am not sure if Xubuntu has as many apps as Ubuntu in its repositories. I basically use my pc for surfing, capture & author video from a camcoder via firewire, ripping DVDs & CDs, mp3s, watch movies, use Open Office etc. I don't use it for mail server or hosting website or play games. Ubuntu does all the above nicely (except Firefox keeps hanging due to flash).

I wonder if Xubuntu can do all that plus recognising my video card - ATI Radeon 7500LE.

Any thoughts or advise is highly appreciated.

Regards. D

---

### Post by eriqjaffe on 2008-08-13
If you already have the full Gnome desktop installed (which you do if you installed the stock Ubuntu environment), you can just enter:

```
sudo apt-get install xubuntu-desktop
```

in a terminal and choose which environment to launch when you log in.  All the apps you have installed in Ubuntu will be available when you log in to Xubuntu.

Recognizing the video card will be independent of the Desktop Environment you use, the drivers are built in to the kernel, or added seperately through the restricted drivers manager or a tool like EnvyNG.

---

### Post by mali2297 on 2008-08-13
Ubuntu, Kubuntu and Xubuntu all use the same repositories. Their differences lie in what is installed by default.

---

### Post by sub2007 on 2008-08-13
> **Dreamerman said:**
> Hi. I've installed Ubuntu on my fastest machine (only a P4 1.8Mhz 1G ram) & think it runs better & faster than XPpro. I am wondering if I should install Xubuntu instead. 

I hear that Xubuntu is lighter on resources compared to Ubuntu so technically I should get better performance.

It is lighter, but it's lightness lies in it's modularity (the fact that you only have a few apps by default and build the system up. An Xubuntu install, in my opinion and especially if you already have GNOME installed is not much lighter than a GNOME install. You still might notice better performance (I did) but it's a trade off that Xfce is a different environment.

> But I am not sure if Xubuntu has as many apps as Ubuntu in its repositories.

The repositories are identical.

> I basically use my pc for surfing, capture & author video from a camcoder via firewire, ripping DVDs & CDs, mp3s, watch movies, use Open Office etc. I don't use it for mail server or hosting website or play games. Ubuntu does all the above nicely (except Firefox keeps hanging due to flash).

I wonder if Xubuntu can do all that plus recognising my video card - ATI Radeon 7500LE.

It won't be any different in that respect. Xfce is just a different desktop environment, everything else (Restricted Device Manager, repositories, software you can run on it etc) is identical.

I use Xfce because I like how it works better than GNOME. By all means try it but don't expect it to be more than what it is.

---

### Post by snowpine on 2008-08-13
You can install whatever windows manager/desktop environment you like over Ubuntu and still use all of the same applications and repositories. Gnome, KDE, and Xfce are the "official" ones, but there are even "lighter" options such as Fluxbox, Openbox, IceWM, etc. 

Fortunately, it is easy to experiment with different WMs without having to reinstall your entire system. The "Sessions" menu at the login screen allows you to choose between whichever options you have installed.

The good news is that your hardware is sufficient to run any "flavor" of Ubuntu, so you can make the choice based on your personal preference. Some people with older computers are "forced" to use Xubuntu because they can't run Ubuntu. You have a choice! :)

---

### Post by Dreamerman on 2008-08-13
Thanks all your posts. Is there a difference between Xubuntu native install vs Xubuntu installing on top of Ubuntu ?

I would imagine full benefits (speed, performance etc) can be reaped by native Xubuntu install rather than one on top of the other.

Thanks D

---

### Post by CarlosNYB on 2008-08-13
I initially installed Ubuntu and just recently added the Xubuntu Desktop via the repositories, and it has been significantly quicker for me, and it's compositing works better for my machine which has one of those on-board graphics cards that doesn't work with Compiz.  Once I figured out how to make a new custom menu in the menu editor I liked the fact it was so easy to save an xml file to one of my own directories for a custom menu, not sure you can do that so easily in Gnome (I tried and just figured I had to use ala cart).

I'm glad to see Fluxbox is in the repositories, I'll have to try that and others, for the sake of comparison.  I didn't think they'd be there!

---

### Post by snowpine on 2008-08-13
> **Dreamerman said:**
> Thanks all your posts. Is there a difference between Xubuntu native install vs Xubuntu installing on top of Ubuntu ?

I would imagine full benefits (speed, performance etc) can be reaped by native Xubuntu install rather than one on top of the other.

No, there is no difference. The system loads only what is needed for your current session, so if you are in Xubuntu, all the Ubuntu desktop packages are just sitting harmlessly on your hard drive. 

Here is an analogy: Both Ubuntu and Xubuntu have exactly the same "engine" but Ubuntu has a heavier (and arguably more comfortable) "chassis" so it moves a little slower. They handle differently, but are the same "under the hood."

---

### Post by Dreamerman on 2008-08-13
> **snowpine said:**
> No, there is no difference. The system loads only what is needed for your current session, so if you are in Xubuntu, all the Ubuntu desktop packages are just sitting harmlessly on your hard drive. 

Here is an analogy: Both Ubuntu and Xubuntu have exactly the same "engine" but Ubuntu has a heavier (and arguably more comfortable) "chassis" so it moves a little slower. They handle differently, but are the same "under the hood."

Wow, your explanation is crystal clear. Ok, I will look for Xubuntu in add/remove & try it out this weekend. I also have a hp Vectra P3 550Mhz 512Mb ram currently chugging along under XP. It is a special purpose machine built for bit torrent only. Old kit but runs 24/7. I will also put Xubuntu on it this weekend. 

Many thanks.

---

### Post by snowpine on 2008-08-13
> **Dreamerman said:**
> Wow, your explanation is crystal clear. Ok, I will look for Xubuntu in add/remove & try it out this weekend. I also have a hp Vectra P3 550Mhz 512Mb ram currently chugging along under XP. It is a special purpose machine built for bit torrent only. Old kit but runs 24/7. I will also put Xubuntu on it this weekend. 

Many thanks.

You're welcome! :) Let me give you one more tip, because you will not find Xubuntu in add/remove. To install Xubuntu, open the terminal and use this command:

```
sudo aptitude install xubuntu-desktop
```

The reason I recommend aptitude instead of apt-get (which will also work) is that, if you don't like Xubuntu, you can easily remove it with:

```
sudo aptitude remove xubuntu-desktop
```

If you use apt-get (instead of aptitude) and ever decide to uninstall, you must remove the Xubuntu packages one at a time. 

Installing Xubuntu over Ubuntu is easy and totally harmless to your system, so have fun!

---

### Post by Dreamerman on 2008-08-13
> **snowpine said:**
> You're welcome! :) Let me give you one more tip, because you will not find Xubuntu in add/remove. To install Xubuntu, open the terminal and use this command:

```
sudo aptitude install xubuntu-desktop
```

The reason I recommend aptitude instead of apt-get (which will also work) is that, if you don't like Xubuntu, you can easily remove it with:

```
sudo aptitude remove xubuntu-desktop
```

If you use apt-get (instead of aptitude) and ever decide to uninstall, you must remove the Xubuntu packages one at a time. 

Installing Xubuntu over Ubuntu is easy and totally harmless to your system, so have fun!

Amazing, thanks. Does aptitude works for all apps ?

---

### Post by snowpine on 2008-08-13
> **Dreamerman said:**
> Amazing, thanks. Does aptitude works for all apps ?

I think so. My previous advice might be a little out of date, though... [http://ubuntuforums.org/showthread.php?p=5368178](http://ubuntuforums.org/showthread.php?p=5368178)

---

### Post by 1ny0urfac3 on 2008-08-13
take a look at crunchbang linux some time when you get a chance

---

### Post by nickgaydos on 2008-08-13
I like both but if you want total performance without installing another window manager...use Xubuntu. The only problem I had with Xubuntu is the lack of support for .deb files from getdeb.

---

### Post by eriqjaffe on 2008-08-13
> **nickgaydos said:**
> I like both but if you want total performance without installing another window manager...use Xubuntu. The only problem I had with Xubuntu is the lack of support for .deb files from getdeb.You **are** installing a different window mananger with Xubuntu.  Ubuntu uses metacity/compiz, Xubuntu uses XFWM.

You should be able to install .debs from getdeb regardless of your DE.  I install them periodically through the terminal, and my system runs straight Openbox.

```
sudo dpkg -i whatever-deb-you-have.deb
```

---

### Post by Dreamerman on 2008-08-14
In terms of support, popularity & longevity, will Xubuntu be as good as Ubuntu ?

---

### Post by mali2297 on 2008-08-14
> **Dreamerman said:**
> In terms of support, popularity & longevity, will Xubuntu be as good as Ubuntu ?

These forums support Xubuntu as well as Ubuntu. If you don't mind using the command line to solve problems, then solutions for Ubuntu will also work for Xubuntu.

Xfce is a small project compared to Gnome and KDE, and has fewer users, but I don't think there is any risk that it will be discontinued any time soon.

---

### Post by FakeOutdoorsman on 2008-08-14
> **Dreamerman said:**
> ... I also have a hp Vectra P3 550Mhz 512Mb ram currently chugging along under XP. It is a special purpose machine built for bit torrent only. Old kit but runs 24/7. ...
A bit of a thread hijack, but here's a good chance to sacrifice some time to the Nerd Gods.  I would get the [minimal install image]("https://help.ubuntu.com/community/Installation/MinimalCD") (or use the Ubuntu alternate cd if you already have it) and install a command-line only system on the torrent machine using rtorrent as the client.  Once everything is setup I would take out the video card since it's a big wattage hog.  Of course some picky motherboards may not start without a video card.  It can then be administered via ssh and sshfs.

[Howto: Use rtorrent like a pro]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/")

---

### Post by moycano on 2008-08-18
> **Dreamerman said:**
> In terms of support, popularity & longevity, will Xubuntu be as good as Ubuntu ?I'm one of those guys who use Xubuntu by choice not by force because definitely fill all my expectations from a kick-*** operative system.

So, naturally, I'll certainly liked if the distro gain popularity... the only back-step I see is "XFCE" doesn't sound as pretty as "GENOME" but work as good as that, or even better =)

:popcorn:

---

### Post by CarlosNYB on 2008-08-21
Xfce is great, yes.  It spurred me to try fluxbox, which I'm really digging right now.  Maybe next I'll try out IceWM.

What I really dig is that my apps are still there and they work, the repositories and the synaptic are still accessible, and if something is weirdly new I can just switch to a session with something I'm more familiar with and then hop on back.  It's neat, I'm not loosing functionality by choosing a different desktop.  Sure I don't want a lot of Gnome or KDE stuff up while I'm running some lightweight WM, but if I need it it works and it works FASTER.  Thunar (I'm liking this) and XFE are nice (though with XFE it switches focus back to the XFE when I open a text file, I must need some command line switch or else it's a bug) alternatives to Nautilus (NOTE: Nautilus should be run with the command '/usr/bin/nautilus --no-desktop' so it doesn't bring in GNOME with it!)

---

### Post by kidux on 2008-08-21
I use Xubuntu by choice as well, and I'm completely happy with it. I don't care much for GDM or Nautilus at all, so XFCE and Thunar suit me just fine. I used the Xubuntu image as I didn't really want the extra stuff loaded with Gnome, not that it has a real impact on your machine, I just prefer to have as little clutter as possible.

---

### Post by Dreamerman on 2008-08-23
I have a stock standard ex-corporate hp Vectra VE P3 550Mhz 512MB RAM with 20G + 10G hdd & DVD ROM. It's my dedicated 24/7 download machine with no monitor/keyboard/mouse.

Hoping to repeat my success in Ubuntu, I installed Xubuntu on it. There are 2 unresolved problems:-

1. The mobo is old, so failed the acpi test. No matter what I do, I can't resolve the error message despite reading all relevant posts. 50% of the time it can't shut down. Restarting is ok.

2. I simple can't get my main Ubuntu machine to remotely control it despite trying out suggestions from this forum.

As it has been running on XP (albeit on a slow pace) prior to Xubuntu, I've decided to "downgrade" back to XP. It is running as it should again under XP & my Ubuntu have no problems RDPing it.

By no means that Xubuntu is no good. I think if I spend another week on it I can get it working like a charm. At the moment I am spending my free time on my main Ubuntu machine & learning how to use it well.

Good luck !!

---

### Post by gjoellee on 2008-08-23
whith your system speccs you wont notice any special difference between Xubuntu and Ubuntu...

---

### Post by EnGorDiaz on 2008-08-23
> **Dreamerman said:**
> Amazing, thanks. Does aptitude works for all apps ?

apitude can cause problems with multiple desktop enviroments i wouldnt really change back just like that

---

### Post by Dreamerman on 2008-08-23
> **gjoellee said:**
> whith your system speccs you wont notice any special difference between Xubuntu and Ubuntu...

You are right - there isn't much difference on my P3. My P4 1.8A Mhz 1G RAM is humming away nicely on Hardy.

---

