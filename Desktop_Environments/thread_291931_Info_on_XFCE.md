---
title: "Info on XFCE"
date: 2006-11-03
forum: Desktop Environments
---

### Post by lemino on 2006-11-03
I'running Gnome right now and I like it pretty much. Moved here from KDE mostly to try it out and got stuck with it. The reasons where curiousity, a liking towards osx and that kind of design but also performance. Now it's possible it's time to take the next step, namely to go from Gnome to something even more lightweight - I'm talking about XFCE. But I have a few questions though:

1. How big is the difference, really, between gnome and xfce. Both the memory and performance-aspect would be nice. I'm trying xfce out from a live-cd right now and from what I can tell it looks pretty much like gnome. Design-wise I don't feel that xfce would be that much of a gain. 

2. Can I install xfce on my current system or do I have to start from scratch again? Is it possible for gdm to handle xfce or does it have its own starter? What's the easiest way to install xfce/xubuntu?

3. I have a fairly fast computer, will the change be noticable? My system is an Athlon 64 3500, 512 mbts ram and a pretty modest graphics card. 

4. How lightweight is xfce really? Compared to the -boxes i.ex.?

---

### Post by kerry_s on 2006-11-03
Xfce is pretty fast & light  compared to gnome or kde. You can install it easily by selecting xubuntu-desktop in synaptic or for terminal>  sudo apt-get install xubuntu-desktop < then just logout and select xfce4 in the session menu and log in.

---

### Post by lemino on 2006-11-03
Will that give me the same result as if I had just installed xubuntu to begin with?

---

### Post by dbd on 2006-11-03
when you run XFCE it will be just the same as if you had just installed, but all your gnome stuff will be taking up hard disk space, info on removing that is here:
 [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

(I'd advise you try out xfce for a bit first to make sure you do want to get rid of gnome).

Also, as for how much faster it will be, you have a pretty good system so for normal desktop use I doubt you will notice the difference, but then again that is just a guess. You might as well try it! :)

---

### Post by mcpish on 2006-11-05
> **lemino said:**
> 

1. How big is the difference, really, between gnome and xfce. Both the memory and performance-aspect would be nice. I'm trying xfce out from a live-cd right now and from what I can tell it looks pretty much like gnome.


Yes and No.  The thing is for some reason, Ubuntu in particular has decided to configure the default look/feel of XFCE similar to Gnome but that isn't really the default XFCE configuration.  In fact I don't like it so I always change the configuration back to what XFCE is supposed to be like.  

XFCE was designed to be a free clone of an older desktop called "CDE" (Common Desktop Environment) which was popular on Unix Workstations in the 1990s (Sun Workstations, SGI, etc).  The idea is that you have a small dock on the bottom, your applications minimize as Icons to the desktop (not launchers like nearly every other OS, ie Mac/Windows,KDE,Gnome).  It also makes full use of the 3 buttons on your mouse to bring up different menus.  There is no Start/Apple Menu/K style icon instead you right click anywhere on the desktop to bring up your menu.  There is also no "task list", instead you centre-click on the desktop to bring up a list of your current open apps.  As I said before, unfortunatly Ubuntu have decided to heavily change the default configuration of their version of XFCE to act/work like Gnome which I feel is a big mistake.  As you pointed out, it kind of gives the false impression that if they are so similar, why bother switching to xfce?  It only takes about 5 minutes to switch it back though.  Basically xfce is not supposed to work anything like Windows/Mac, it's supposed to work like CDE (Graphical Unix Workstations) which is a completely different behavior than most people are used to, which is probably why the developers thought it was a good idea to make xfce work like Gnome.  But if you get used to the way CDE/XFCE work, you'll love it.

---

### Post by shunthemask on 2006-11-05
> **lemino said:**
> 
1. How big is the difference, really, between gnome and xfce. Both the memory and performance-aspect would be nice. I'm trying xfce out from a live-cd right now and from what I can tell it looks pretty much like gnome. Design-wise I don't feel that xfce would be that much of a gain. 

If you are looking for something that looks entirely different than gnome and pretty, I would go for [fvwm-crystal]("http://fvwm-crystal.org/"), [enlightenment]("http://www.enlightenment.org"), or [fluxbox]("http://www.fluxbox.org") and mod the heck out of it.  Otherwise, and I have no data to back it up, xfce feels much faster and lighter than gnome, but the version that ships with xubuntu does have a memory leak.

> **lemino said:**
> 
2. Can I install xfce on my current system or do I have to start from scratch again? Is it possible for gdm to handle xfce or does it have its own starter? What's the easiest way to install xfce/xubuntu?

To try out the xubuntu desktop on your gnome installation just:
```
sudo aptitude install xubuntu-desktop
```
and make sure that you use **aptitude** for easy removal if you don't like xfce!  I know for a fact that xfce works with gdm, I think it works with kdm.

> **lemino said:**
> 
3. I have a fairly fast computer, will the change be noticable? My system is an Athlon 64 3500, 512 mbts ram and a pretty modest graphics card.

Dunno, I can tell the difference on a Sempron 2800.

> **lemino said:**
> 
4. How lightweight is xfce really? Compared to the -boxes i.ex.?

Again, I have no data, but I felt that fluxbox is that much lighter than xfce than xfce is lighter than gnome.  And fvwm-crystal felt just about as light as fluxbox, but it's prettier out of the box.

Hope I helped.

---

### Post by lemino on 2006-11-05
Thanks for all the info! Just one thing: does it matter if I use apt-get, aptitude or synaptic? Or are they just three sides of the same coin? ;)

---

### Post by shunthemask on 2006-11-05
> **lemino said:**
> Thanks for all the info! Just one thing: does it matter if I use apt-get, aptitude or synaptic? Or are they just three sides of the same coin? ;)

Definitely use aptitude. [Check out this link to figure out why.]("http://psychocats.net/ubuntu/puregnome")

---

### Post by lemino on 2006-11-06
Is it a correct assumption that a more lightweight WM also is less heavy on the battery (if you have a portable)?

---

### Post by lemino on 2006-11-06
> 
Quote:
Originally Posted by lemino View Post
1. How big is the difference, really, between gnome and xfce. Both the memory and performance-aspect would be nice. I'm trying xfce out from a live-cd right now and from what I can tell it looks pretty much like gnome. Design-wise I don't feel that xfce would be that much of a gain.

If you are looking for something that looks entirely different than gnome and pretty, I would go for fvwm-crystal, enlightenment, or fluxbox and mod the heck out of it. Otherwise, and I have no data to back it up, xfce feels much faster and lighter than gnome, but the version that ships with xubuntu does have a memory leak.

How serious is this memoryleak? Should I try a different version? Is it usable as standard-wm?

---

### Post by shunthemask on 2006-11-08
> **lemino said:**
> Is it a correct assumption that a more lightweight WM also is less heavy on the battery (if you have a portable)?

I don't think that a lighter wm would have a positive effect on the battery, unless you are hitting that swap very heavily.

> **lemino said:**
> How serious is this memoryleak? Should I try a different version? Is it usable as standard-wm?

Well, I am using the beta 1 version right now, the one that ships with Xubuntu 6.06, and I have 512 MB of memory.  Currently, I have to log out every week or two because I start swapping too much.  Before my other dimm gave out and I had a gig of memory, I never had to do anything of the sort.  So, I would say that the leak is an annoyance, but no more than that.  The latest version of xfce is 4.4rc2, but I can't get my jumpdrives to automount in thunar on that bad boy, so I am using the distro version currtently.  Supposedly, the memory leak is fixed in the rc2 version.  I'm hoping that 4.4 goes gold before feisty fawn freezes.

---

### Post by undead-monkey on 2006-11-09
I like XFCE alot, even in Xubuntus default config. If you want real light weight, FluxBox is the way to go. 
On the Linux partition on my Macbook I just have gnome and Fluxbox as my WMs, but on MacOSX under parallels I have installed just about every usable WM for ubuntu including Enlightenment 16 and E17 (not too stable, but fast and flashy).
Fluxbox is great, XFCE is easy, and much faster than gnome, but not nearly as quick as Fluxbox.

I say try them all, then decide.

---

### Post by rplantz on 2006-12-05
> **mcpish said:**
> Yes and No.  The thing is for some reason, Ubuntu in particular has decided to configure the default look/feel of XFCE similar to Gnome but that isn't really the default XFCE configuration.  In fact I don't like it so I always change the configuration back to what XFCE is supposed to be like.

I liked CDE. To minimize the changes, would it be better to install xfce instead of xubuntu?

---

