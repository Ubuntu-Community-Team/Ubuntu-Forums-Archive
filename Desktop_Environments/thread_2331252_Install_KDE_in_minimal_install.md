---
title: "Install KDE in minimal install"
date: 2016-07-20
forum: Desktop Environments
---

### Post by Bucky Ball on 2016-07-20
As per the title.

Been diddling about with Virtualbox and that's all good. Was looking at a live session of Kubuntu in VBox last night, just for the heck of it and out of curiousity, when I had a thought. Being a minimal install/Xubuntu-core person, wonder how you'd install a minimal install and add KDE, the Kubuntu desktop environment? This has nothing to do with VBox, don't need help with that, so to avoid confusion best to forget about that aspect of this thread. It is solely about installing KDE in a mini.iso install. :)

So, started digging and all very confusing. I can't see that there's a way that will just install the KDE DE in any way similar to how you might install lxde or xfce4, for instance by using 'sudo apt install xfce4' or installing xfce4 from a package manager ... its that simple. Is there a way to install just the KDE DE that is that quick and simple or is there something hidden in a Kubuntu repo I haven't discovered yet or have overlooked?

My intention was to install the mini.iso as a virtual machine, then add what I want, in this case, KDE and a few apps. Although I know a few essential Kubuntu bits and pieces are unavoidable (install xfce4 and you get Thunar and some other bits and pieces also), I am not interested in installing the full suite of default Kubuntu apps (just like I'm not interested in installing the full default suite of Xubuntu apps, which is why I use xfce4 only, not a regular Xubuntu). Don't know anything about them and not interested in using them. 

Hopes are fading. All thoughts and ideas appreciated.

---

### Post by vasa1 on 2016-07-20
> **Bucky Ball said:**
> ...
Hopes are fading. ...
Subscribing all the same ;)

---

### Post by Bucky Ball on 2016-07-20
:) Just wanting to set up a virtual machine for web browsing and doodling about safely online and thought KDE looked interesting, might use that as it's something different. Don't like lxde or Unity or many of the others I've tried. I only use xfce4, have done for years, so a change is as good as a holiday. Don't want to go there on my host machine, just the guest.

Failing this I might give Gnome a blast. I'm suspecting that can be installed fairly easily, and just the DE, but will persist with this for a day or two and see what pops up here.

---

### Post by vasa1 on 2016-07-20
KDE is even more famous (?) than GNOME for its dependencies.

The LXQt guys, in anticipation of Wayland, are hoping that the KDE people can further trim kwin's dependencies but that's taking time.

---

### Post by Bucky Ball on 2016-07-20
Yea, generally I avoid installing anything that starts with 'K' for that very reason. It opens the floodgates to a swathe of other things starting with 'K'! One of the reasons I have my doubts about this. Love xfce4, but a change is as good as a holiday and just after the possibility of taking one when I feel like it (a delicious concept when applied to the analogue world also). :)

Maybe I'll have better luck after the trimmings ... when and if that time arrives ...

---

### Post by Bucky Ball on 2016-07-21
Just thought I'd bump this in a last gasp attempt and also to say thanks for the KDE/Wayland info, vasa1. ;)

---

### Post by Irihapeti on 2016-07-21
You could try installing kde-baseapps and see what that gets you. Then you could add other packages as needed.

Sometimes I install stuff with --no-install-recommends to minimise the amount of extra stuff that gets installed.

I've tried that with Unity and Openbox (plus Xubuntu) but not with Kubuntu or kde.

---

### Post by Bucky Ball on 2016-07-21
Tnx, Irihapeti. I had looked at going in that direction earlier, kdebaseapps, but for some reason convinced myself that was going to drag in something similar to kubuntu-desktop, which I don't want. Re-investigation and re-thinking, on the strength of your suggestion, I think not. I am in the process of installing the mini.iso as a virtual machine and will proceed to try kdebaseapps with --no-install-recommends and post the outcome.

At the moment the install is locked at 6% while installing the base system, so could be a long ride ... :)

---

### Post by Bucky Ball on 2016-07-21
* Update. Well ...

Currently, have successfully installed the mini.iso as guest and successfully booting and logging into the CLI. All is as expected and working fine. My issue is I can't get to a desktop.

Tried installing Lightdm. On reboot, get the purple 16.04 splash forever. Tried sddm, which I'd never heard of, and that takes me to a terminal, no login GUI then plasma(?) desktop. Any ideas? I was looking for the DE that is the current Kubuntu default, thinking that was kdm, but appears it is now sddm? 

Bit stuck, but on the right track, I think. With the --no-install-recommends there was not a huge load of data installed. :)

FTR, I installed using

```
sudo apt install kdebase-apps --no-install-recommends
```

I'm wondering if, just like when I build an xfce4 install from the mini, there are some essential things that are up to the user to install that I don't know about in Kubuntu/KDE and/or this command has overlooked. :-k

---

### Post by Bucky Ball on 2016-07-22
Well, I got there, sort of.

In a nutshell, to get there I installed Ubuntu minimal, didn't select a machine profile in tasksel. Once installed, rebooted and logged in to the CLI I installed kdebase-apps, sddm, kubuntu-desktop, all with --no-install-recommends, and have wound up with a desktop environment with not very much else and have little idea of what I'm doing with it, not being familiar with KDE or Kubuntu! :-k :)

I did other things along the way, but removed the changes if they didn't work, and it took some (quite some) hours to get here. Think I only really needed to install those three in the end. I have a snapshot of the machine  taken before I added anything to the mini.iso install, so might go back and retrace my steps.

My issue now is that I can't get the virtual machine to go full screen (Virtualbox goes full screen fine when you hit RightCtl+f but not Kubuntu, if you know what I mean), but that is the stuff of a new thread, so for now, thanks to both of you for your input.

I maybe could have gone lighter but don't know enough about what KDE requires to get to a desktop, so for now, Bucky's Kubuntu-core takes its wobbly first steps!

(Is it Muon or can I use Synaptics?)

---

### Post by robbie 348 on 2016-07-22
Bucky Ball, have you looked at KDEneon? It was on distrowatch a week or two ago and looked minimal-ish, Rob.

---

### Post by Bucky Ball on 2016-07-22
> **robbie 348 said:**
> Bucky Ball, have you looked at KDEneon? It was on distrowatch a week or two ago and looked minimal-ish, Rob.

Yes, I did look at that earlier in the piece. Not for me but thanks. :)

---

### Post by Irihapeti on 2016-07-22
> **Bucky Ball said:**
> Well, I got there, sort of.

... I maybe could have gone lighter but don't know enough about what KDE requires to get to a desktop, so for now, Bucky's Kubuntu-core takes its wobbly first steps!

(Is it Muon or can I use Synaptics?)

That's where the real fun begins - working out what you do and don't need. VBox makes it a lot easier to backtrack and try again. I had several goes before I happened on a minimal Xubuntu that did what I wanted. Ditto with Openbox.


Maybe it's time I tried Kubuntu as well... :)

---

### Post by vasa1 on 2016-07-22
> **Bucky Ball said:**
> ...
(Is it Muon or can I use Synaptics?)
I'm not trying to mess with you but why install either? I have Synaptic Package Manager installed but hardly ever use it. Mostly just *apt-get whatever* (yes, I know just *apt* exists), *apt show* and *apt search* with an occasional *apt-cache policy*, *apt-cache depends* and *apt-cache rdepends* get me through the day.

But, if you really want, I'd say go with Muon purely in the spirit of this being a KDE venture.

---

