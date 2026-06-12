---
title: "Lubuntu, fluxbox... + netbook"
date: 2011-02-07
forum: Desktop Environments
---

### Post by vacco on 2011-02-07
I have an Atom N450 based Acer eMachines netbook on its way to me in the mail. It comes preinstalled with Win7 Starter, but having run Ubuntu nicely (kind of) on my main laptop for the past months, I think I will throw Ubuntu with some lightweight GUI on it.

I have seen some people criticize XFCE for becoming increasingly heavy lately, so I thought I should try something even more lightweight. Lubuntu/LXDE looks promising, but I have been wondering if I can manage with only a window manager. So far Fluxbox looks promising, but I find it very impractical to go via the whole programs menu for everything I want to do. Is there no way to ease access to frequently used applications such as the web browser?

Also, I see that Fluxbox have not been updated in 2-3 years, which makes me worry about problems with for example getting security updates. I am also going to have a look at IceWM.

Any thoughts on this? Suggestions?

---

### Post by Copper Bezel on 2011-02-07
Well, I'm on an Eee S101 running the full Gnome DE, with full Compiz desktop effects, including transparent menus with alpha blur, and it's a very responsive machine regardless, so. Um. I think you're overcompensating.

Granted, it's based on flash memory and has 2G of RAM installed, but still, it's the same 1.6 Ghz Atom processor.

---

### Post by wizard10000 on 2011-02-08
Allow me to share my own netbook's desktop - that's a full KDE desktop with desktop effects enabled using only 183mb of RAM  :D

[IMG]http://ebassist.com/pix/htop.jpg[/IMG]

---

### Post by Terminal Upper Case on 2011-02-16
My 100 pesos:
I'm running Lubuntu on a Samsung N210, which has the same CPU as you, vacco. I've been playing around with a lot of different distros lately, and I honestly couldn't be happier with this one. The alpha version of Xubuntu 11.04 seems a lot more promising than the 10.10 Xubuntu edition, once the bugs get ironed out, but honestly, LXDE totally and completely rules. It's so flipping fast, and pretty much cruft-free. It does everything I need it to at twice the speed as the other guys, and is a pretty much painless drop in for the Gnome environment with equivalent features and methods. And because it's a(n unofficial) Ubuntu based distro, it's way easier to find drivers and stuff directly geared to your netbook, and it doesn't include all the rest of the garbage.
I've been looking at Fluxbox myself, which I installed on Lubuntu, and the learning curve is a bit steep to get beyond the single menu control and into full functionality, but it seems to offer limitless potential/possibilities, kinda like emacs. Right now I'm working my way through the Fluxbox wiki.
Seriously, dropping Gnome was the best thing I ever did. I can do far more useful stuff now. And as for using KDE, well that's just nuts. On any machine and for any reason.
ps: stay away from any *buntu option mentioning a netbook remix. It will break *everything*.
pps: as for the age of the stable Fluxbox version, the wiki recommends getting the development version, which is current and apparently pretty stable anyways.

---

### Post by ve4cib on 2011-02-16
I think Fluxbox is small enough that security issues are pretty much a non-issue with it.  It's really not many steps above the raw X-window manager; just some window decorations, toolbars, and root menu added on top, really.  So don't let the relative lack of recent updates scare you off.

Something I've started doing on my (very) old Toshiba laptop is to use Fluxbox with LxPanel running within it.  It's an odd combination, but it works very well.  Configure Fluxbox to have no toolbars, and put lxpanel in the startup script and away you go.  It's easier to use than straight fluxbox, and offers a little more in the way of useful toolbars and buttons.

I've played around with LXDE a little bit, and it seemed decent.  I could certainly get used to using it.  I've heard that Lubuntu isn't necessarily the best LXDE-using distro though.  You may be better off doing a Debian install and putting LXDE on that.  Or a command-line Ubuntu install, with a manual installation of LXDE and whatever other applications and services you need.  That way you get only what you actually want, and not all the other "bloat" (for lack of a term I loathe less) that can creep in with default installations.

---

### Post by Terminal Upper Case on 2011-02-16
@ve4cib a command-line ubuntu distro sounds intriguing. Would you recommend a particular one?
The reason I endorse a *buntu distro over a Debian one or otherwise in this case, is the ad hoc repositories that make the backlight and some of the other features work as expected for my netbook don't seem to work with Debian, at least as far as I was able to determine. The Eee might very well be different. Personally I'd prefer to run FreeBSD if I could figure out how to achieve the same functionality.

Side note: The Maverick Meerkat repository seems to contain the August 07, 2010 build of Fluxbox, which is a lot newer than the last "stable," in case you don't feel like building from the current git source for whatever reason.

---

### Post by vacco on 2011-02-18
I was indeed considering the Ubuntu CD with no extra software.

I installed Fluxbox from the repo and had a look at it the other day, playing with the config file etc, and I must say it looks pretty cool.

Does anyone have experience with Fluxbox and WLAN? Last time I was at the tech support office on campus, which was overstaffed at the moment, one of the guys there was spending the idle time trying to set up WLAN in Fluxbox on his Linux box, but apparently had a hard time with it.

---

### Post by snowpine on 2011-02-18
> **vacco said:**
> Does anyone have experience with Fluxbox and WLAN? Last time I was at the tech support office on campus, which was overstaffed at the moment, one of the guys there was spending the idle time trying to set up WLAN in Fluxbox on his Linux box, but appearantly had a hard time with it.

Fluxbox is very cool. :)

If you don't like configuring WLAN from the command line, simply install a network applet like 'network-manager' or 'wicd'.

---

### Post by ve4cib on 2011-02-18
> **Terminal Upper Case said:**
> @ve4cib a command-line ubuntu distro sounds intriguing. Would you recommend a particular one?

Personally I just use the Ubuntu Alternate Install disc.  Usually I just use whatever the latest LTS release is since it's mostly a recovery/tinkering tool, and not something I use for regular, everyday use -- remember I install the CL system onto a 2GB thumbdrive and then install X + fluxbox + applications on top of that.  If you wanted to use a non-LTS release it should work the same.  It would just be "obsolete" sooner -- if that matters to you.

The advantage of going for the Ubuntu CL install option over another distro (like DSL, Puppy, TinyCore, etc...) -- in my view -- is that since I'm already used to Ubuntu I have instant access to their repos, which makes installing stuff I'm used to easier.  And when you have to deal with restricted drivers (Nvidia, Broadcom, etc...) that makes live *so* much easier.



> If you don't like configuring WLAN from the command line, simply install a network applet like 'network-manager' or 'wicd'.

+1 for WICD.  It's a great little network manager.  Fewer dependencies than nm-applet, but does effectively the same thing; sits in the tray and lets you configure your LAN/WLAN settings.  What more could one ask for?

---

### Post by vacco on 2011-02-18
What terminal application do you use for that? ifconfig?
Isn't network-manager the one used by Ubuntu (Gnome)? The tech support guy had Fluxbox installed next to Gnome, and so got the network up and working, but could not configure it from within Fluxbox as far as I remember.

---

### Post by snowpine on 2011-02-19
> **vacco said:**
> Isn't network-manager the one used by Ubuntu (Gnome)? The tech support guy had Fluxbox installed next to Gnome, and so got the network up and working, but could not configure it from within Fluxbox as far as I remember.

If network-manager is already installed, simply launch it with "nm-applet". You can put "nm-applet &" in your ~/.fluxbox/autostart.sh if you like.

---

### Post by wizard10000 on 2011-02-19
> **vacco said:**
> What terminal application do you use for that? ifconfig?
Isn't network-manager the one used by Ubuntu (Gnome)? The tech support guy had Fluxbox installed next to Gnome, and so got the network up and working, but could not configure it from within Fluxbox as far as I remember.

And they pay him to do tech support?

Sheesh.

---

