---
title: "Will switching to Lubuntu really make my notebook faster?"
date: 2017-04-12
forum: Desktop Environments
---

### Post by second.exodous on 2017-04-12
So first off I'm trying to get my system the fastest it can be for Openshot.

I read Linux Lite ran a lot faster on hardware but it uses LTS releases and when I use a Ubuntu derivative I have problems getting some software running if it isn't the latest release.  I do like how it turns off a bunch of stuff that runs in the background, and I thought that is what made it run leaner than Ubuntu, not just the desktop environment.

My notebook fans come on full blast just when I'm browsing the web so I'm wondering if I should run something lighter than Ubuntu, if a desktop environment will be enough by switching to Lubuntu, or maybe manually turn off processes in Ubuntu.  What is recommended?

Thanx,
Stan

---

### Post by Bucky Ball on 2017-04-13
I recommend starting with nothing and working your way up rather than installing a full-blown OS and trying to work your way down. 

You can use the [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD"). That gives you the kernel and that's it. On first boot after install, you will get a cursor in a CLI. From there, away you go. Install a desktop environment (lxde or xfce4 are light and from Lubuntu and Xubuntu respectively) and openshot and you're away.

The other option is to install [Lubuntu-core]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") or [Xubuntu-core]("http://xubuntu.org/news/introducing-xubuntu-core/") (there is a link to ready-made community ISOs at the bottom of that page; very handy ... I use Xubuntu-core on all my machines, but prior to that started with the mini.iso and worked up to it). 

Lubuntu-core or Xubuntu-core will both install a very basic system with a desktop, a few default bits and pieces and little else. You install the apps you want (Synaptic, Firefox, openshot, whatever) and start with installing from a terminal. I usually go for Synaptic Package Manager and take it from there.

Hope that helps and good luck.

(PS: IMHO, if you are looking to do audio/vid production/editing, Ubuntu is definitely not the place to be. A much lighter desktop, like lxde or xfce4 is much more suitable on a lighter install. You will take note that Ubuntu Studio (a full install of that is complete overkill), which is solely devoted to AV production uses xfce4 desktop environment, NOT Unity, as used by Ubuntu.)

---

### Post by Autodave on 2017-04-15
I run Xubuntu 16.04 on an Asus EEEPC: 900mhz with one gig RAM. Not the fastest machine, but still way faster than when Win XP was on it.

---

### Post by gordintoronto on 2017-04-15
A fan running full blast might mean there's a heat issue, usually caused by dust buildup on an older laptop.

You could install lm-sensors, run sensors-detect, say "yes" to the final question where the default is "no." After a reboot, you can run sensors to see temperatures, voltages and fan speeds.

---

