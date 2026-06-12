---
title: "128MB RAM, P3 700Mhz: Ubuntu vs Xubuntu?"
date: 2009-02-10
forum: General Help
---

### Post by nickpick on 2009-02-10
What do you think? I, generally speaking, prefer GNOME to XFCE, but since the machine has mere 128MB RAM, I'm not entirely sure whether it can run it properly.

---

### Post by hikaricore on 2009-02-10
Try Xubuntu.

I have a server at my office with similar specs...
However you may want to consider using an alternate WM such as fluxbox or openbox.

This will free up a lot more of your system's resources for other applications.

Also be aware that you will need to install from an alternate cd as 128mb of ram is not enough to boot a livecd.

---

### Post by neur0 on 2009-02-10
Minimum system requirement for installing xubuntu is 192 MB RAM.
Although you can use alternate install CDs ([https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)) you could try the Ubuntu based Crunchbang linux ([http://crunchbanglinux.org/](http://crunchbanglinux.org/)) (although Openox can be confusing for you, it is really  lightning fast)
Or try my favourite for XFCE on older machines: Zenwalk ([http://www.zenwalk.org/](http://www.zenwalk.org/))

---

### Post by JK3mp on 2009-02-10
I'd just go get at least a 1gig stick of RAM...they usually only run around 25 bucks now..memorys alot cheaper than it used to be.

---

### Post by jespdj on 2009-02-10
But beware that the most common type of RAM in use nowadays (DDR2) will most likely not fit in an old PC, and the right kind of RAM module will be harder to find and cost more.

---

### Post by mb_webguy on 2009-02-10
I just installed Openbox and Xfce.  Openbox is nifty, but I couldn't figure out how to connect to my wireless network (in the scant few minutes I spent using it).  If I could've, I'd be tempted to use it on occasion.  I'll probably try it again later when I have more time to play with it.  

Xfce, which is somewhat similar, connected automatically, just as in Gnome.  I'm using it right now.  It's a bit like Openbox with some features of Gnome.  For example, it's menu is more like Gnomes, though you access it the same way as in Openbox.  Xfce also has a desktop with icons, which Openbox didn't seem to have.

Both are noticeably speedier than Gnome (as you'd expect, considering how much more lightweight they are).

EDIT:  I take it back.  Openbox connected to my network too, it just didn't inform me of it.  Openbox is very cool, and I can see using it on a more regular basis.  It's very clean and very quick.  While I wasn't the one looking for a different desktop, thanks for the suggestion, neur0.

---

### Post by sanderj on 2009-02-10
> **nickpick said:**
> What do you think? I, generally speaking, prefer GNOME to XFCE, but since the machine has mere 128MB RAM, I'm not entirely sure whether it can run it properly.

From [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

"Minimum system requirements
<snip> Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM."

So: get the needed RAM. Otherwise don't bother to run xUbuntu on 128 MB RAM system.

---

### Post by mb_webguy on 2009-02-10
Do a minimal installation following [these directions]("http://www.psychocats.net/ubuntu/minimal"), but use Openbox rather than IceWM.  Your system should be plenty capable of using Openbox, and Openbox is easy to configure if you don't mind editing a couple of xml files.

---

### Post by kerry_s on 2009-02-10
> **nickpick said:**
> What do you think? I, generally speaking, prefer GNOME to XFCE, but since the machine has mere 128MB RAM, I'm not entirely sure whether it can run it properly.

those are the exact same specs as my ibm t20.
i used arch linux, jwm for my window manager, pcmanfm for filemanager, leafpad for editor, firefox, xpdf, abiword, gnome-mplayer, etc...
i use the arch netcfg for wireless, zd1211 based usb dongle.

it runs just fine, i set mine up for my niece to use, shes a major youtube fiend, she watches vid after vid, plays those disney flash games.

---

### Post by snowpine on 2009-02-10
Puppy or DSL should run well on those specs. Don't bother with anything in the 'Buntu family, in my opinion, unless you can get more ram.

---

### Post by JK3mp on 2009-02-10
As i said...just GET MORE RAM!...the most it'll cost you is 50 bucks. I know thats alot to some people..but for a perfectly well working computer it'll be worth the time you'll save hassling with it due to lack of memory.

---

### Post by nickpick on 2009-02-10
> **JK3mp said:**
> As i said...just GET MORE RAM!...the most it'll cost you is 50 bucks. I know thats alot to some people..but for a perfectly well working computer it'll be worth the time you'll save hassling with it due to lack of memory.

Thanks for the tip (and thanks to everybody else too), but the problem is that the motherboard simply won't accept more than 128 MB. It's a pretty old notebook, which used to run Win2k original and now runs on XP.

I'm assuming that the standard-issue Xubuntu will be able to boot (not live) on the specified system. Can I generally speaking await higher performance than on the currently installed XP SP3?

---

### Post by mb_webguy on 2009-02-10
> **nickpick said:**
> I'm assuming that the standard-issue Xubuntu will be able to boot (not live) on the specified system. Can I generally speaking await higher performance than on the currently installed XP SP3?

Probably, since the combination of Linux and the Xfce desktop environment uses fewer resources than XP.  But as with everything in life, there are no guarantees.

---

### Post by doorknob60 on 2009-02-10
I'm setting up Arch on a very similar build (P3 667 mhz, 128 MB RAM) and it works fine. I had Debian on it yesterday but managed to screw it up. Had Opera and Fluxbox on it and it was suprisingly fast actually. This will probably end up even faster, since Arch is awesome like that. Avoid Ubuntu and Xubuntu with anything less than 256 MB of RAM, unless you're going minimal and setting up Openbox or something like that. I can recommend you Crunchbang: [http://crunchbanglinux.org/](http://crunchbanglinux.org/) Based on Ubuntu 8.10 I'm pretty sure, and it uses Openbox and it's light. I tried it in Virtualbox it was good. I recommend Opera over Firefox though, on slow systems Opera shines.

---

### Post by mb_webguy on 2009-02-10
Actually, it might be a good idea to do a minimal installation of Ubuntu and install Openbox.  It's a window manager rather than a full desktop environment, and therefore uses considerably fewer resources.  The main difference between a window manager like Openbox and a complete desktop environment like Xfce is that you don't have anything like a taskbar (though in Openbox you can access the "start" menu by right-clicking on the desktop), and you don't have any icons on the desktop (though you still use graphical file managers).  It takes a little getting used to, but it can certainly be worth it, especially on a resource-light system.

Actually, I've installed Xfce and Openbox on my computer -- I'm acutally using Openbox right now -- and Openbox is noticeably faster than Xfce, and considerably faster than Gnome or KDE.

---

### Post by snowpine on 2009-02-11
> **nickpick said:**
> Thanks for the tip (and thanks to everybody else too), but the problem is that the motherboard simply won't accept more than 128 MB. It's a pretty old notebook, which used to run Win2k original and now runs on XP.

I'm assuming that the standard-issue Xubuntu will be able to boot (not live) on the specified system. Can I generally speaking await higher performance than on the currently installed XP SP3?

I predict that Xubuntu will be slower than Windows on your computer, as you do not meet the ram recommendation of 256mb. A lightweight distro such as DSL, SliTaz-loram, or Puppy would be more appropriate than anything in the 'Buntu family.

---

### Post by nickpick on 2009-02-12
> **snowpine said:**
> I predict that Xubuntu will be slower than Windows on your computer, as you do not meet the ram recommendation of 256mb. A lightweight distro such as DSL, SliTaz-loram, or Puppy would be more appropriate than anything in the 'Buntu family.

Once again, thanks to everybody who responded.

It's not for me, but for my mom. I've been using Ubuntu for a while now and what I like about it is a good package manager (with all the software she could easily install), regular updates, etc. The problem is that as of late, it takes pretty long for her comp to load pretty much any modern website (i.e. I send her a link, 3 minutes later it displays the contents). I like OpenBox, but it's just not Windows-ish enough. XFCE and GNOME on the other hand are pretty similar. Any other ideas? Would switching off a bunch of services help?

EDIT: Actually, ignore that. Adding gRun and gnome-panel to OpenBox makes it perfectly usable.

---

