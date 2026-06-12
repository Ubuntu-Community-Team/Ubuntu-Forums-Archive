---
title: "Converting a regular Ubuntu to Kubuntu"
date: 2010-12-01
forum: Desktop Environments
---

### Post by isecore on 2010-12-01
Due to Ubuntu ditching Gnome and going for Unity instead, I'm contemplating moving to Kubuntu instead. I figure it's as easy as uninstalling all the Ubuntu-related packages and installing kubuntu-related ones instead.

Installing Kubuntu is a breeze - kubuntu-desktop fixes most of this. Now I just need to figure out the smoothest way of purging all the Ubuntu/Gnome-packages and converting this all out to Kubuntu. That's where I need your tips!

I'm going to attempt this first inside a virtualboxed Ubuntu I've setup explicitly for this experiment.

So, how do you figure the smoothest way of going about this would be?

---

### Post by Brandon Williams on 2010-12-01
When did Ubuntu ditch Gnome? I know that the the netbook remix moved to Unity, but the standard ubuntu-desktop did not, at least not in 10.10. Are you specifically referring to running UNR and switching to running kubuntu in a netbook specific mode?

---

### Post by InTheMarket on 2010-12-01
> **Brandon Williams said:**
> When did Ubuntu ditch Gnome? I know that the the netbook remix moved to Unity, but the standard ubuntu-desktop did not, at least not in 10.10. Are you specifically referring to running UNR and switching to running kubuntu in a netbook specific mode?

11 is gonna go Unity too. 

OP, try this. It should work on Lynx.
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Then do this to avoid desktop clutter (only run gnome or only run KDE at once)
[http://www.makeuseof.com/tag/switch-gnome-kde-45-ubuntu-1004/](http://www.makeuseof.com/tag/switch-gnome-kde-45-ubuntu-1004/)
You can choose "KDE" as the default display manager.

---

### Post by isecore on 2010-12-01
The plan is for 11.04 to make Unity the default DE for the standard Ubuntu-distribution. Since I have a deep dislike for Unity I'm looking for alternatives. I'd rather hop to another DE rather than switch distro, thus this posting.

> **Brandon Williams said:**
> When did Ubuntu ditch Gnome? I know that the the netbook remix moved to Unity, but the standard ubuntu-desktop did not, at least not in 10.10. Are you specifically referring to running UNR and switching to running kubuntu in a netbook specific mode?

---

### Post by Brandon Williams on 2010-12-01
Yep ... got it now. I hadn't seen the news that they're moving to Unity instead of going to Gnome shell.

Getting rid of all the extra gnome stuff can be a pain if the packages aren't marked as having been auto-installed. One way to start removing everything is to first mark all the dependencies and recommendations of the ubuntu-desktop meta-package as auto-installed and then delete ubuntu-desktop. When you remove ubuntu-desktop, all its dependencies and recommendations will be remove as long as no other package also depends on them.

I use aptitude for package management. In case you don't use aptitude, the process would be to: 1) find the ubuntu-desktop package, 2) press enter to go to the info window, 3) scroll down to the "Depends" line, 4) press M to mark all dependencies auto-installed, 5) scroll down to the "Recommends" line and press M again, 6) press q to return to the main list, 7) press - to mark ubuntu-desktop for removal, and finally 8) press g twice to perform the removal.

This might not get everything, but it's a good start.

---

### Post by qamelian on 2010-12-01
> **isecore said:**
> The plan is for 11.04 to make Unity the default DE for the standard Ubuntu-distribution. Since I have a deep dislike for Unity I'm looking for alternatives. I'd rather hop to another DE rather than switch distro, thus this posting.
You're not being entirely accurate. Ubuntu is *not* dropping Gnome. They are just replacing the default GUI. All the Gnome stuff under the hood remains. For the record, I'm no fan of Unity either and the regular Gnome desktop will still be installable if you prefer to use that instead of Unity. Personally, I'll be sticking with Gnome-shell. :)

---

### Post by isecore on 2010-12-02
Yeah, I know this. But it's not default, and I'm worried that support for Gnome then will become less than stellar and relegated to some kind of "alternative" environment. Plus, I'm not into Gnome-shell either. So Kubuntu seems to be the least painful alternative for me.

> **qamelian said:**
> You're not being entirely accurate. Ubuntu is *not* dropping Gnome. They are just replacing the default GUI. All the Gnome stuff under the hood remains. For the record, I'm no fan of Unity either and the regular Gnome desktop will still be installable if you prefer to use that instead of Unity. Personally, I'll be sticking with Gnome-shell. :)

---

### Post by cascade9 on 2010-12-02
> **isecore said:**
> Yeah, I know this. But it's not default, and I'm worried that support for Gnome then will become less than stellar and relegated to some kind of "alternative" environment. Plus, I'm not into Gnome-shell either. So Kubuntu seems to be the least painful alternative for me.

You might find a minimal install + xfce4 (or even xubuntu-desktop) is closer to what your are used to. 

Not that I'm trying to stop you from using KDE 4.X, its what 'm using ;)

---

### Post by qamelian on 2010-12-02
> **isecore said:**
> Yeah, I know this. But it's not default, and I'm worried that support for Gnome then will become less than stellar and relegated to some kind of "alternative" environment. Plus, I'm not into Gnome-shell either. So Kubuntu seems to be the least painful alternative for me.
I can understand what you're saying, but support for Gnome can't decrease, because everything other than the GUI is still Gnome. I just find it strange that you would want to make a change that involves a lot more work than just switch to the "old" Gnome look! It's like you'd prefer to make a 100% change in your environment, instead of just replacing the 5% that bugs you. There are people that have done that all along. People who prefer compiz or openbox instead of Metacity, for example. :)

If all you like is what's on the surface, I guess it won't matter. But if you like Gnome because of how it works "under the hood", be prepared to relearn a lot of stuff when you move to KDE. The two environments have vastly different philosophies in some ways. They've both good, but different.

---

### Post by isecore on 2010-12-02
I would prefer to have it exactly the way I have it right now. But no matter how I twist and turn I will have to either adapt to an environment I don't like, or hack it. If Gnome will still be easily installable EXACTLY as it is now (i.e. 2.x series) then fine, I might hold off.

But it's also about demonstrating my annoyance at this move. Sure, I could just sit quiet, and of course I know that for all the pull I have it might as well be a fart in a supernova, but I feel I must draw the line here.

I'm not going to do this tomorrow, and I'm going to hold off until a while after 11.04 has been released. If I can keep stuff the way it is now, then fine. But I want to be prepared if I feel that things need to be changed. Forewarned is forearmed, if you ask me.

> **qamelian said:**
> I can understand what you're saying, but support for Gnome can't decrease, because everything other than the GUI is still Gnome. I just find it strange that you would want to make a change that involves a lot more work than just switch to the "old" Gnome look! It's like you'd prefer to make a 100% change in your environment, instead of just replacing the 5% that bugs you. There are people that have done that all along. People who prefer compiz or openbox instead of Metacity, for example. :)

If all you like is what's on the surface, I guess it won't matter. But if you like Gnome because of how it works "under the hood", be prepared to relearn a lot of stuff when you move to KDE. The two environments have vastly different philosophies in some ways. They've both good, but different.

---

