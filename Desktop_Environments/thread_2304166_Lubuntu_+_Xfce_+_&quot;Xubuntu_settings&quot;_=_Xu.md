---
title: "Lubuntu + Xfce + &quot;Xubuntu settings&quot; = Xubuntu?"
date: 2015-11-24
forum: Desktop Environments
---

### Post by Sweet_Baby_Jamie on 2015-11-24
Hi, please forgive a question from a "sort of" newbie.  I have a Lubuntu respin on my older desktop and really like it.  But just for grins I wanted to check out Xfce4, so I used Synaptic to install Xfce4 and a package called **xubuntu-default-settings**.  I did not want Xubuntu, so I didn't install the *xubuntu-desktop* megapackage.  I assumed (correctly?) that the *xubuntu-default-settings* package just has stuff like panel placement, theme, etc.  I like the screenshots I have seen of Xubuntu so I wanted my Xfce4 desktop to look like it, but my poor old computer would be slower on Xubuntu judging my the system requirements described on the Xubuntu web site.

I'm noticing only a very little difference in speed during my "xubuntu sessions," mostly only that some applications are a teeny bit slower to launch.  But then they run just as responsively as they do in my LXDE sessions.

So my questions are,

1 - I didn't install Xubuntu on accident, did I?

2 - Do the *xubuntu-default-settings* make Xfce4 more resource hungry than "plain vanilla" Xfce4?

---

### Post by buzzingrobot on 2015-11-24
I'd say "No" and "almost certainly not".

xubuntu-desktop-settings would add some xubuntu artwork and themes, plus a few small settings and utility packages, to the XFCE4 environment you'd already installed.

The differences you're seeing may be due to the different window manager (xfwm vs openbox) and the fact that even xfce4 is just a bit more demanding than lxde.

BTW, You can visit the Ubuntu Package Search site at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to search and review any and all packages in the repos for all active Ubuntu releases.  You clean burrow through and see listings of a package's dependencies, their dependencies in turn, change logs, etc. 

apt-get can be used in simulated mode which will perform a simulation of actions that would occur and display the resulting feedback without actually doing or changing anything. So, "**sudo apt-get -s install xubuntu-default-settungs" **would go through the motions of installing that package, with the same feedback and notices displayed, but not change your system.

---

### Post by Dennis N on 2015-11-24
Installing xfce4 would have been enough. It installs all the basic packages for an xfce desktop. But it is not Xubuntu, which includes additional user software. So the answer to question #1 is no. the answer to #2 is also no because xfce4 depends on xubuntu-default-settings, meaning it would be installed whenever you install xfce4.

---

### Post by Bucky Ball on 2015-11-24
> **Dennis N said:**
> Installing xfce4 would have been enough.

That's it. That's all you need. xfce4 is 'self-contained'. You don't need to install anything else. I'd get rid of the xubuntu-settings whatever ... :)

Your slowdowns could be caused with a confusion between the lubuntu-settings and the xubuntu ones. Better without the latter.

---

### Post by Sweet_Baby_Jamie on 2015-11-25
Thanks!  Very helpful!

---

