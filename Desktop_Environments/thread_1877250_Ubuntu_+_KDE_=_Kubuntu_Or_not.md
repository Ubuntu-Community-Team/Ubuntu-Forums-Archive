---
title: "Ubuntu + KDE = Kubuntu? Or not?"
date: 2011-11-07
forum: Desktop Environments
---

### Post by zcacogp on 2011-11-07
Hello, 

I am aware that I am about to ask a question which may seem quite ... basic ... but I'm going to ask it anyway. Are you sitting down? Good. Here goes ...

What is Ubuntu? And what is Gnome? And what is KDE? 

(I did check that you were sitting down!)

I've been using Ubuntu since a while ago, and never got on with Unity in 11.04 - but I could bypass it. 

I'm now up to 11.10 on my desktop (I also have a couple of laptops - more of them later), and not getting on with Unity in the same way. I'm in the process of trying other windows managers; Enlightenment (which seemed lovely, but too alien for me), and now KDE. So, to be clear, I have KDE installed on Ubuntu 11.10, and when I log in I can choose Unity, Unity2D or KDE Plasma. 

I'm loving KDE. No two ways about it. I'm still in the early stages, but it seems to suit me better than Unity does. BUT, I am not quite sure what I actually have. Do I have Ubuntu, or do I have a (home-brewed) Kubuntu? When I boot up, and when I close down, I see a 'Ubuntu' splash-screen, but is this just branding? 

I still have to do some playing with my Ubuntu/KDE chimera before I am completely settled with it, but I am looking to rebuild the two laptops I own. My question is whether I should do as I have done with my desktop (Ubuntu 11.10, with KDE installed later), or whether to download and put Kubuntu on from the outset. If I go the Kubuntu route, what will I notice that is different from Ubuntu? Will I need to learn a different set of commands to use in the terminal? (For instance, will 'sudo apt-get update && sudo apt-get upgrade' work, and what about 'gksudo gedit XYZ'?) Will things appear more different 'under the skin' - things like Samba and fstab and so on? Or will this sort of stuff be the same as in Ubuntu? 

And another Q. One of my lappies (the one I am using to write this - and probably my favourite) is an old thing, with a single 1.4Gig processor and a mere 750Meg of memory. Am I right in guessing that it would struggle to run Ubuntu with KDE/Kubuntu and that I would be better off thinking about something like Puppy Linux? (It wouldn't run Unity in Ubuntu 11.04 - another reason why I went back to Gnome in that version.) 

Apologies for the slightly dumb questions. If it's easier to point me to a webpage where this sort of thing is explained clearly then please do ... 

Thanks. 


Oli.

---

### Post by sanderd17 on 2011-11-07
If you install Kubuntu, you will have a bit lighter system than Ubuntu+KDE. All gnome programs won't be installed.

So that also answers a part of your second question, you won't need to learn other commands, but you can't use gnome-programs either. So
```

sudo apt-get blablabla

```
will work. but
```

sudo gedit text.txt

```
won't because Gedit is a Gnome program.

Instead of that, you should use
[/code]
sudo kate text.txt
[/code]

You can also install Gedit if you want. But one Gnome program will make your system a lot heavier since it will pull a lot of Gnome libraries with it.

All CLI things are the same, but graphical things are different.

For your lappie, 750 meg is a bit low for Ubuntu, but I believe Xubuntu and Lubuntu will both run smoothly on it. There's no need to use Puppy.

In other words:

Ubuntu is an OS: a kernel with applications installed on top of it.
Gnome is a desktop environment (DE): some program that manages your workflow (your menus, rendering ...). Normally it uses an own window manager (some program that renders the windows) and it has an own set of default apps (like gedit, nautilus, empathy, gparted ...). Ubuntu doesn't give your the full Gnome experience, because they change some of the default apps. Like Epiphany is dropped in favour of Firefox.
KDE is just another DE with it's own apps and window manager.

---

### Post by zcacogp on 2011-11-07
Sanderd17, 

Thanks - that was a really useful reply. It helped a lot. 

You talk about gnome programs - something I hadn't thought about. Am I right in guessing therefore that both Gnome and KDE have their own sets of programs (with equivalents - gedit for kate, as an example you used) and if you have both gnome and kde installed then you can access the programs for either of them, from either 'side'? However if you only have one installed then you only have the set of programs associated with that environment, clearly. 

You talk about Xubuntu and Lubuntu - I guess that the relationship between them and their window managers is similar to that between Ubuntu and Kubuntu? (If Gnome is to Ubuntu as kde is to Kubuntu, what are their equivalents for Xubuntu and and Lubuntu? Lubuntu is lde - non? What about Xubuntu? Xfe?) 
[I]
Ubuntu is an OS: a kernel with applications installed on top of it.
Gnome is a desktop environment (DE): some program that manages your workflow (your menus, rendering ...). Normally it uses an own window manager (some program that renders the windows) and it has an own set of default apps (like gedit, nautilus, empathy ...). Ubuntu doesn't give your the full Gnome experience, because they change some of the default apps. Like Epiphany is dropped in favour of Firefox.
KDE is just another DE with it's own apps and window manager. [/I]

That was particularly helpful, thanks. I guess I didn't fully understand the difference between a Window Manager and a Desktop Environment, and was (mentally) interchanging the terms. 

Are there any good websites with some nice simple explanations where I can read around this sort of stuff? 

Thanks again. 


Oli.

---

### Post by techvish81 on 2011-11-07
desktop environment for lubuntu is lxde,  it is a very light de compared to others.  
for xubuntu it is xfce,  not as light as lxde but lighter than other,  

for your 750meg PC lubuntu is a better choice. 

search in Google with terms like Linux desktop environments etc.. u will get many sites explaining,  reviewing , suggesting DEs

---

### Post by drawkcab on 2011-11-07
I would pair up Lubuntu with Thunar (xfce's file manager) for that older lappie.  LXDE might strike you as basic in some ways but it's about getting the job done when resources are tight.

---

### Post by viperdvman on 2011-11-07
I like running the KDE desktop environment. However, I don't run Kubuntu. I run Ubuntu 11.04, which **does** have Unity, but also has GNOME as a fallback. And I run GNOME as my primary desktop environment. But I wanted to play around with KDE quite a bit without having to install Kubuntu alongside it, so I just installed the **full** KDE desktop environment alongside my Unity and GNOME. So my desktop environment choices are: Ubuntu (Unity), Ubuntu Classic (GNOME), and KDE Plasma.

That's the beauty of having Ubuntu... you can install any version of it (Ubutnu, Kubuntu, Xubuntu, Lubuntu) and then install any desktop environment on top of it :)

for your 768MB system, Xubuntu should work very nicely. Good luck with your choices. :)

---

### Post by zcacogp on 2011-11-08
Chaps, 

Many thanks for your replies and recommendations. Very helpful indeed. 

I'll look at LXDE and XFCE and have a think. I am guessing that the windows manager is a large part of the system load presented by any *buntu package, in that smaller ones can have a big effect on the overall system footprint? 


Oli.

---

### Post by vanhenryjr on 2011-11-08
I have some of the same questions. I am running ubuntu 11.04 on a sys76 laptop. I have unity. I think I have gedit. Do I have GNOME? Or maybe is unity gnome? or does unity contain gnome?
thanx

---

### Post by sanderd17 on 2011-11-08
> **vanhenryjr said:**
> I have some of the same questions. I am running ubuntu 11.04 on a sys76 laptop. I have unity. I think I have gedit. Do I have GNOME? Or maybe is unity gnome? or does unity contain gnome?
thanx

Unity is a shell on top of Gnome (I know, it's quite complicated).

So Unity uses a lot of Gnome code, but they also have (obvious) differences.

---

### Post by SeijiSensei on 2011-11-08
> **zcacogp said:**
> You talk about gnome programs - something I hadn't thought about. Am I right in guessing therefore that both Gnome and KDE have their own sets of programs (with equivalents - gedit for kate, as an example you used) and if you have both gnome and kde installed then you can access the programs for either of them, from either 'side'? However if you only have one installed then you only have the set of programs associated with that environment, clearly.

It's not only the programs, like gedit vs kate, but the various libraries required to run GNOME or KDE programs.  I always install from the Kubuntu distribution CD/DVD, but I often add a few programs that require GNOME like synaptic or gnumeric.  The first time you install a GNOME program, apt will list a number of other pieces of software that need to be installed as well called "dependencies."  Adding other GNOME programs might bring in a couple other specific libraries, but the bulk of the added software will already be installed.

The same holds true in reverse if you install a KDE program like dolphin or ktorrent on a GNOME system.  

KDE has some special controls for how GNOME programs are managed on the desktop.  Take a look in System Settings > Desktop Appearance > GTK+ Appearance to see these controls.

---

