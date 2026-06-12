---
title: "What are the differences between X Window System and Window Managers"
date: 2009-08-18
forum: Desktop Environments
---

### Post by jocampo on 2009-08-18
I've read several articles recently and still I am confused about the differences and purposes of: X Window System, Window Managers, Logon Screen Managers, etc. I am just trying to fully understand how they interact each other and what are the lightest and better options (combination for me)

For instance... i thought KDE was a complete option that comes with its own Window Manager: kwm. But I installed antiX mepis lastnight on a modest machine I have and found that it uses KDE with IceWM. :confused: ... did they removed kvm but keep KDE as Desktop environment?

Also..on same machine, I installed as 2nd option, LinuxMint, which uses FluxBox as Window manager (lighter and faster than IceWM ?) ... but is slow as hell for my 256 RAM machine; opening the browser takes several seconds and swaps into disk as crazy, not the same on antiX. Yeah, I noticed default browser on antiX is not Firefox... but I had the idea Fluxbox was lighter.

So ... can someone explain the differences, possible combinations, etc? I love Ubuntu with Gnome, but with 256 of RAM runs slow. Could be possible uses Gnome with IceWM?

Thanks,

---

### Post by XubuRoxMySox on 2009-08-18
> **jocampo said:**
> I've read several articles recently and still I am confused about the differences and purposes of: X Window System, Window Managers, Logon Screen Managers, etc.

A window *manager* is the system that governs window size and behavior, and themes and fonts (to some extent).

A *desktop environment* is a whole 'nother animal that works *with* a window manager and sets up libraries and stuff that enable integration with certain applications. **KDE**, for example, is a pretty and very popular *desktop environment* that comes with many of it's own applications like K-Mail, Konqueror (combination web browser and file manager), K-write, K-this and K-that. They're very good and very powerful and versatile applications! And KDE is gorgeous with it's plasmas and widgets. But it's a resource hog (not lightweight by any means). I dislike the KDE applications, sweet and powerful though they are, because it just looks and feels like "AOL for Linux" or something to me. It's just a matter of personal taste, mind you... there are lots of folks who love KDE, and for good reason.

**Gnome** is also a *desktop environment* and like KDE, many applications are Gnome-based and depend on that environment. Gnome is less resource hungry than KDE I think, but for some reason in Linux Mint, the Gnome environment consumes resources very heavily. They will tell you the problem is "upstream" (their way of blaming Ubuntu for the problem because Mint is 99.9% Ubuntu), but Gnome in Ubuntu is not nearly so demanding on resources.

**Xfce** is also a *desktop environment*, and much more lightweight than either KDE or Gnome. It "pulls in" dependencies and it's own libraries and file manager and applications, however.

What you're looking for is an *independent* desktop environment that pulls in as few dependencies as possible. I have found one that makes my low-resource old Dell Dimension run at mind-bending speed and pulls in *very* few dependencies. It is *much more lightweight* than even Xfce, and is super-simple to use (great for n00bs!). It works best with the uber-lightweight window manager called Openbox. It's called [LXDE]("http://lxde.org") and is available in Ubuntu's repositories. It installs effortlessly in seconds by opening a terminal and entering

```
sudo apt-get install lxde
```

Now mind you, you don't need a desktop environment at all to run a super-lightweight, high-speed Linux. Desktop environments are often the single biggest drain on a computer's resources (except LXDE, which is barely a d.e. at all). Openbox can run independently and offers  stark and minimal beauty all it's own. By far the best implementation of bare-bones Openbox's power and versatility is the Ubuntu-based distro called [Crunchbang Linux]("http://crunchbanglinux.org"). Just have a look... it keeps many old computers out of the landfill and makes them run as fast and impressively as a new Vista box!

But if you need a desktop *environment* (as I do) for simplicity (and for multiple users who just have to have "something to click on"), I wholeheartedly recommend LXDE.

I use a minimal Ubuntu/LXDE mixture to make a super-newbie-friendly warp-speed-fast os for my old computer. It rawks and the other kids love it. They don't even know it's Linux unless I tell them.

Minimal Ubuntu with LXDE will make your old 256 RAM machine sing! As will Crunchbang Linux, which offers all the power of Ubuntu (plus codecs and stuff already preinstalled) with none of the "bloat" caused by desktop environment dependencies.

Cheerfully,
Robin

---

### Post by mcduck on 2009-08-18
X is used with any of them, it's the base on top of which all the graphical desktops on Linux are built.

[http://en.wikipedia.org/wiki/X_Window_System]("http://en.wikipedia.org/wiki/X_Window_System")

Gnome, KDE, XFCE and LXDE are desktop environments. Desktop environment is a complete setup that includes window manager, file manager, configuration tools, background services, applications etc, everything you need for a full-blown desktop experience. (Even though all these things come as a package, that doesn't mean you couldn't still replace different components with something else, like for example using a different window manager than what the desktop environment would use by default)

Fluxbox, Openbox, IceWM etc. are window managers. Basically window manager is only responsible of putting your running programs inside a window that you can move around, although many of them include some kind of menu that you can use to start applications, sometimes other tools as well. For example Fluxbox comes with it's own panel.

Different combinations? There are as many as you can imagine. Pick the components you like and combine them together as you wish.


What comes to Firefox being slow on your LinuxMint setup, blame Firefox. Running a lightweight desktop environment or window manager won't make your programs any lighter. Firefox is still exactly the same Firefox, and has the habit of using quite a lot of RAM and also a lot of CPU power if you try to use sites that include heavy Flash or JavaScript.

Gnome with IceWM? Possible, although there are probably better options than IceWM if you want to make your Gnome lighter. Openbox is a fairly common option, but if you really like IceWM then go for it. :)

---

### Post by anticapitalista on 2009-08-18
antiX does not come with kde, but comes with icewm and fluxbox (toggle F1 at login screen if you want fluxbox)

antiX uses iceweasel (Debian's debranded firefox).

If you want a light gnome (ubuntu-based) give Debris a try.
It is very good IMO.

[http://debrislinux.org/](http://debrislinux.org/)

(You can also install gnome on antiX. Use the meta-installer app)

---

### Post by jocampo on 2009-08-18
Folks ... 1st ...thanks a lot for all your comments; I learned something new from each one ;-) ...

Yeah, I know Firefox is "heavy" but still the overall performance for LinuxMint is not the best when tested (same machine again antiX)

So far, in that low RAM machine (which still, has a not so slow P4 2.8 Ghz processor) I've tried: FluxBuntu, antiX, Xubuntu. And this is my preference (so far, in order) with a few comments ...

antiX
Like it a lot! I can browse internet, open editor and terminal and feels good with just 256 of RAM. The idea of conky on it by default is nice. And comes with really cute wallpapers. I am really impressed! 

Xubuntu
An official Ubuntu flavor. It is kind of heavy foe being lightweight, but so easy to use. I really like Canonical products. Best linux experience today.

FluxBuntu
I was so excited when I saw the screenshoots online... but damm it :-( ... my Linksys wifi adapter does not work. I tried to configure via console with no success. Maybe I'll give a try this weekend.

I think that, at the end, I'll keep antiX and will install Xubuntu as dual boot but I just downloaded CrunchBang; sounds like light enough but with some media additions that catch my attention a lot..

---

### Post by flux_user on 2009-08-21
To re-iterate what others have stated in a different fashion:

1) You have Desktop Environment (D.E. or  DE) such as Gnome, KDE, XFCE.  DE are full blown GUI environment with tools etc.  DE's can/do have Window Managers incorporated with them.  Gnome  actually uses MetaCity as it's Window Manager (previously SawFish) Well, that is beside the point; sorry don't mean to confuse the issue.   Off topic and irrelevant : I miss Sawfish.

2) You have Window Managers (W.M or WM).  The sole purpose of a Window Manager is to open up windows.  They are minimalistic by design.  

For what it's worth I have an older laptop and I am running Ubuntu and have 512 megs  of ram.  I have made a few changes:
1) Fluxbox as my GUI
2) disabled some services (don't do this unless you know what you're doing)
3) I have installed some other lighter resource applications.
4) Yes Firefox 3.x is slow on this:

cat /proc/cpuinfo | grep name
model name      : Intel(R) Pentium(R) III Mobile CPU      1200MHz

You can use  Ubuntu but using some Window Manager that uses less resources and lighter weight applications does help (a lot).  This is what I use and it may help or give you some ideas.

1) Fluxbox for GUI
2) XFE for a file manager not Nautilus.
3) Thunderbird is a littler lighter than Evolution; but not as light as claws mail.  I need some of the formatting features in Thunderbird but I love claws.
4) Xterm not gnome terminal

Some other things that I have noticed for my older laptop.  Do not try this if you don't know what I am talking about or what is listed in this bug report.  My xorg settings had to be changed to get better performance with my older IGP (integrated graphics processor or video card).  

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/363238](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/363238)

Making a few change to xorg made improvements to my system as well as all the other items listed above.  EXA was causing a problem on my ATI card so I switched to XAA.

A description of other  Window Managers and Desktop Environments can be found here:

[http://xwinman.org/](http://xwinman.org/)  Excellent resource for Window Managers and Desktop Environments:  As you and others have mentioned; Fluxbox, IceWM and others are faster. 

With respect to: *"But I installed antiX mepis lastnight on a modest machine I have and found that it uses KDE with IceWM.  ... did they removed kvm but keep KDE as Desktop environment?"*

AntiX uses Fluxbox and IceWm and Mepis uses KDE.  These are both on mepis' site; but they are two different products.  Yes, I used AntiX on this machine.

With respect to: *Also..on same machine, I installed as 2nd option, LinuxMint, which uses FluxBox as Window manager (lighter and faster than IceWM ?) ..*.

Both Ice and Fluxbox are fast... do you really need to know which one is a millisecond faster  than the other  one?  Pick the one that is fast and usable (to you) and has the features that you require.  Both are excellent choices and have excellent support; both are under strong developer communities.

*opening the browser takes several seconds and swaps into disk as crazy, *

I have the same issue with Firefox on both AntiX and Ubuntu; it's a combination of machine age and memory.  Pick a lighter browser.  If I remember correctly; AntiX uses Dillo and I switched it to Firefox because I need adblock plus and noscript.  :-)  You won't have that problem if you have dillo on your  Ubuntu machine; Opera is also quite fast.  Check out your browser options; it's all in synaptic or apt-get install "WhatEverApp".

Now with respect  to:  [I]Could be possible uses Gnome with IceWM?

You can "potentially" swap out the  Window Manager aspect of Gnome which is MetaCity to IceWM.  That  is an aspect you can change; how hard is it on Ubuntu? That I don't know.  Can you combine IceWM and Gnome? YES according to icwwm.org: *"# Usable with GNOME and KDE environments"*
[/I]

I am not sure how much of a performance boost you can get from swapping out MetaCity to IceWM... 

PS: I know I need to learn not to say: "Now with respect  to:"

I hope I clarified some things.... well... at least I hope I did...

PS: I wish Ubuntu officially supported fluxbox as a disto.  Well, if anyone with pull is reading this... :-) That would make me :-)

Regards

---

