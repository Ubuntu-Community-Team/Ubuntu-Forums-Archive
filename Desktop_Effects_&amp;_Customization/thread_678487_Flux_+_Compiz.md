---
title: "Flux + Compiz"
date: 2008-01-25
forum: Desktop Effects &amp; Customization
---

### Post by Ross M on 2008-01-25
Hello,

Is it possible to install Flux with Compiz on top?

Thanks,
Ross

---

### Post by rosegarden78 on 2008-01-26
Yes but you need to start with Ubuntu GG 7.10 desktop first.  Check [here]("http://ubuntuforums.org/showthread.php?t=385981") and [here]("http://ubuntuforums.org/showthread.php?t=677959").  Why fluxbox?  XFCE is the way to go!

---

### Post by Ross M on 2008-01-26
> **rosegarden78 said:**
> Why fluxbox?  XFCE is the way to go!
I've been using linux as server software (no GUI) for a few years now.  I finally decided to switch over to Linux as my desktop platform and I wanted something different than CentOS (which I use for my web servers, mail srvrs, etc.).  I don't like the orange/brown theme that Ubuntu comes with so I looked around.  I've used blackbox on windows before and I just like the feel of it.

Just a personal taste really.

---

### Post by gtrtx on 2008-01-26
Actually, you cannot run Fluxbox with Compiz as both are windows managers. You can only run one window manager at a time. 

You can run Compiz with a desktop environment such as Gnome, KDE or as mentioned ,XFCE.

---

### Post by yabbadabbadont on 2008-01-26
The only way to get true transparency with Fluxbox is to use xcompmgr and transset.

See the following for details: [http://fluxbox-wiki.org/index.php/Transparency](http://fluxbox-wiki.org/index.php/Transparency)

Note that the article may be a bit outdated, but the fundamental information is correct.

---

### Post by rosegarden78 on 2008-01-26
> **gtrtx said:**
> Actually, you cannot run Fluxbox with Compiz as both are windows managers. You can only run one window manager at a time. 

You can run Compiz with a desktop environment such as Gnome, KDE or as mentioned ,XFCE.

Yes come to think of it that's what the error message said when I tried it, compiz unable to run because of other window manager present.  But I think he wants a headless system or server.  Does Blackbox count as 'headless' because it's a WM just like Xfce?

Perhaps a straight Ubuntu Server edition is best.  It has a terminal login right?  But if you want a 'black box' with Compiz and Avant then the [links]("http://ubuntuforums.org/showthread.php?t=677959") [above]("http://ubuntuforums.org/showthread.php?t=385981") provide exactly that for me.

---

### Post by nfox on 2008-03-30
Yes it does work with Gutsy with ease. If it's not working for you, you've got a setup issue. I'm using Flux right now, with Compiz and Kdesktop and it's way faster than a full KDE or Gnome session.

I've got Kubuntu Gutsy installed, apted Flux and when I right click, the Fluxmenu has Compiz and KDE as options for window managers. 

Also, why do people say XFCE is so fast? I'd like to see some proof of it running any faster than Gnome or KDE. Flux, IceWM, etc. are the fastest in my experience.

---

### Post by Triggerhapp on 2008-03-30
> **nfox said:**
> Also, why do people say XFCE is so fast? I'd like to see some proof of it running any faster than Gnome or KDE. Flux, IceWM, etc. are the fastest in my experience.

IceWM and Fluxbox are Window managers (WM's) although KDE, Gnome and Xfce are Desktop Managers, with a Seperate WM running underneath it.

IceWm and fluxbox, naturally, will run faster than XFCE, but XFCE is the current fastest DM out there.
Xfce uses alot less Memory than either too.

---

### Post by mcduck on 2008-03-30
> **Ross M said:**
> I've been using linux as server software (no GUI) for a few years now.  I finally decided to switch over to Linux as my desktop platform and I wanted something different than CentOS (which I use for my web servers, mail srvrs, etc.).  I don't like the orange/brown theme that Ubuntu comes with so I looked around.  I've used blackbox on windows before and I just like the feel of it.

Just a personal taste really.

If your only real issue is the color theme, just get another one :D

There are hundreds of different GTK themes available at gnome-look.org, quite many in Ubuntu repositories, couple already installed by default and if that's not enough at least Clearlooks and Glossy support changing their colors in the theme selection window..

Same applies to icons and window themes.

---

### Post by nfox on 2008-03-30
Yea, Flux isn't a DM but the definition starts to get blurred a bit. Since KDE loads KDesktop to handle icons and all, the actual desktop in desktop manager is seperated. So Flux users may run iDesk and I don't see a difference really except in semantics. 

I know it's a bit more complicated than that but for the end-user there isn't much difference.

---

### Post by Triggerhapp on 2008-03-30
infact, its crystal clear, but not to those of us who dont program it...
As far as im aware, Nautilus is the DM for Gnome, Not sure on KDE, didnt stay with it more than 50 minutes :P, and Xfce uses xfdesktop(4?) 
The window managers are metacity, kwin and xfwm4, respectively.
To be totally honest, when you run Compiz on Gnome, you might as well argue that the only truely gnome bits are Nautilus and gnome-panel. 
Although not having run Fluxbox, i know for a fact that Icewm is a Windowmanager, controls its own panels/menu and draws on the root window

---

