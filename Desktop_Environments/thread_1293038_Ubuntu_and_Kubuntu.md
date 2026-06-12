---
title: "Ubuntu and Kubuntu"
date: 2009-10-16
forum: Desktop Environments
---

### Post by Shibblet on 2009-10-16
Are there any differences between Kubuntu and Ubuntu (Besides the desktop) on a fresh install of either?

---

### Post by amingv on 2009-10-16
> **Shibblet said:**
> Are there any differences between Kubuntu and Ubuntu (Besides the desktop) on a fresh install of either?

The desktop environment and the default programs that come with it are the only difference, as far as I understand.
At kernel level, they're pretty much the same.

---

### Post by Shibblet on 2009-10-16
That's what I figured.  Although, I am having an issue with downloading the kernel update.  The 4 files are blocked for some reason.  Nice big candy-like red "X".

I'm wondering if loading Ubuntu, then downloading Kubuntu-Desktop is the better way to do this.  So if I ever need to do a system update, I can jump into Gnome to download my packages.

Is there an "Add/Remove Programs" type app for KDE?  The one there now is a lot more like Synaptic.  It more reminds me of the downloader for Mandriva.

---

### Post by vinutux on 2009-10-16
> **Shibblet said:**
> Are there any differences between Kubuntu and Ubuntu (Besides the desktop) on a fresh install of either?

All new features tested ubuntu first the applied to kubuntu mostly like compiz......you can easily install all of them from kubuntu desktop

---

### Post by airbag on 2009-10-16
do you recommend just going in to package manager in ubuntu and downloading/installing kubuntu-desktop? im a newbie to this but it feels like there are different opinions on how to do this.

---

### Post by Shibblet on 2009-10-16
> **airbag said:**
> do you recommend just going in to package manager in ubuntu and downloading/installing kubuntu-desktop? im a newbie to this but it feels like there are different opinions on how to do this.

That might be what I do.  But the only thing I've noticed by doing that is that your KDE Packages are available in your Gnome menus and vice versa.

---

### Post by amingv on 2009-10-16
> **Shibblet said:**
> That's what I figured.  Although, I am having an issue with downloading the kernel update.  The 4 files are blocked for some reason.  Nice big candy-like red "X".

I'm wondering if loading Ubuntu, then downloading Kubuntu-Desktop is the better way to do this.  So if I ever need to do a system update, I can jump into Gnome to download my packages.

Is there an "Add/Remove Programs" type app for KDE?  The one there now is a lot more like Synaptic.  It more reminds me of the downloader for Mandriva.

That has happened to me with kernel upgrades, too.
Usually I just install them from the console or directly in Aptitude/Synaptic and they come up fine. Not sure why this happens, though.

About "Add/Remove Programs", I haven't seen such an app in KDE (can't say I've searched, either) but I think if you install synaptic you can use gnome's.

> **airbag said:**
> do you recommend just going in to package manager in ubuntu and downloading/installing kubuntu-desktop? im a newbie to this but it feels like there are different opinions on how to do this.

If you are going to use just KDE, I am of the opinion you do a fresh install of Kubuntu, it's a lot less messier.
If you want to use both, then installing kubuntu-desktop is the way to go.

---

### Post by slakkie on 2009-10-17
KpackageKit, although it might not work smoothly, so I've read. You might want to google it to see how people responded to it. I prefer the cli for package managment. 

I use Kubuntu, and the main differences are the default apps you get installed. Kubuntu uses network-manager, just like gnome does, it just has a different applet.

Just give it a spin :)

---

### Post by garvinrick4 on 2009-10-17
I have selected KDE from Ubuntu packages and it gives you kde and all its dependencies and a selection at log in to go to either Ubuntu or Kubuntu. It gives you a kubuntu log in splash then KDE  or Gnome desktop. It was nice to take a peek at and mess with then throw away. Had to do fresh install to get rid of Kubuntu log in screen. I just like Gnome much better and never did get good looking Konqueror browser, fonts stayed bit-mapped and never clear type. Could have been me I disliked it.

---

### Post by Shibblet on 2009-10-17
> **amingv said:**
> If you are going to use just KDE, I am of the opinion you do a fresh install of Kubuntu, it's a lot less messier.
If you want to use both, then installing kubuntu-desktop is the way to go.

I'm finding out, after a clean installation of Kubuntu, that most of the programs in the repository are made for Gnome.  So when I pick a program like Emesene, or Mplayer it downloads a bunch of Gnome packages...  So I guess I have to like it messy.  ;)

There is a bit of a learning curve to KDE also.  Mainly just finding where certain things are at, and a couple of application differences.  

I am really enjoying KWin over Compiz.  I have no tearing issues with video playback, although it does seem like some of my video is playing back a bit choppy, or skipping frames.  This is even with VDPAU and Smplayer.  Can anyone shed some light on this?

---

### Post by lovinglinux on 2009-10-17
> **Shibblet said:**
> That might be what I do.  But the only thing I've noticed by doing that is that your KDE Packages are available in your Gnome menus and vice versa.

You can install kde-core instead of kde-desktop ([see more info here](http://www.psychocats.net/ubuntu/kde-core)). That will add only the basic necessary stuff to run KDE, so your menu won't get too crowded.

You can also launch plasma over Gnome, on the same session. I have posted a tutorial for Karmic Koala [here](http://ubuntuforums.org/showthread.php?t=1291048).

---

### Post by maestrobwh1 on 2009-10-18
I use Kubuntu... I just think KDE4 is slick and it seems a more intuitive move for someone that might be coming from windows.

I do notice that the menu editor for kde has and option for menu entries for "show only in KDE" so that might be helpful in one direction.  It is also simple enough to use the menu editor, create a sub folder and move the gnome apps there for the kde menu.

I run a partially mixed system.  I run Samba and nautilus lets me mount and unmount my shares listed in fstab... On my eee-pc, I run eeebuntu (ubuntu for the eee-pc) that uses gnome, but I have amarok and kaffeine installed there.

It will be a bit cluttered if you insist on having both complete desktops... and you will probably have to choose whether you want gdm or kdm as your greeter.

---

### Post by Shibblet on 2009-10-19
> **maestrobwh1 said:**
> I use Kubuntu... I just think KDE4 is slick and it seems a more intuitive move for someone that might be coming from windows.

I'm finding that Gnome is a lot more "simplistic".  And that's not a bad thing.  My main reason for switching from Ubuntu to Kubuntu is the Window Manager.  Compiz is still just a bit too buggy for me,  I love the compiz-effects and such, but it messes with Video playback.  KWin doesn't seem to have the same problems, and you still get most of the effects.

> **maestrobwh1 said:**
> I run a partially mixed system.  I run Samba and nautilus lets me mount and unmount my shares listed in fstab... On my eee-pc, I run eeebuntu (ubuntu for the eee-pc) that uses gnome, but I have amarok and kaffeine installed there.

I've thought of installing Ubuntu, then dropping in the KDE Desktop, but there's really no need for me. 

Although, why doesn't Kubuntu have an app installer like Gnome-App-Install?  All it really has for package management is a KDE version of Synaptic.

---

### Post by lovinglinux on 2009-10-19
> **Shibblet said:**
> I am really enjoying KWin over Compiz.  I have no tearing issues with video playback, although it does seem like some of my video is playing back a bit choppy, or skipping frames.  This is even with VDPAU and Smplayer.  Can anyone shed some light on this?

I have the same tearing problem on every clean install, using nvidia graphics card. It's due to nvidia direct rendering permissions. To fix it, read [this](http://ubuntuforums.org/showpost.php?p=7950332&postcount=2).

Works every time for me.

---

### Post by Shibblet on 2009-10-19
> **lovinglinux said:**
> I have the same tearing problem on every clean install, using nvidia graphics card. It's due to nvidia direct rendering permissions. To fix it, read [this](http://ubuntuforums.org/showpost.php?p=7950332&postcount=2).

Works every time for me.

I don't have the tearing issues with Kubuntu.  But I get occasional frame-rate loss (choppy frames).  Will that post of yours solve the frame rate issues.

And just out of curiosity, with an Nvidia card, don't you want to keep direct rendering?

---

### Post by lovinglinux on 2009-10-19
> **Shibblet said:**
> I don't have the tearing issues with Kubuntu.  But I get occasional frame-rate loss (choppy frames).  Will that post of yours solve the frame rate issues.

I didn't have bad video frame-rate, but I was experiencing bad frame-rate and high CPU usage when spinning the cube. That solution fixed this too, so I guess it could help you. 

> **Shibblet said:**
> And just out of curiosity, with an Nvidia card, don't you want to keep direct rendering?

Yes, that fix is to regain direct rendering.

---

