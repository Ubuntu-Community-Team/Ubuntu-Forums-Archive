---
title: "Kubuntu/KDE, Xubuntu/XFCE - are they same or which is better?"
date: 2010-06-05
forum: Desktop Environments
---

### Post by murthy on 2010-06-05
After installing ubuntu, if one wants to try other desktop variants, whether installing KDE-desktop / XFCE-desktop over ubuntu is the same as installing Kubuntu / Xubuntu over ubuntu?  If not, what is the difference, which is better?

---

### Post by beastrace91 on 2010-06-05
The only difference between them is their desktop environment. Which is "better" really depends on what you are looking for on your particular system.

Give them both a try and check them out. Personally I run Kubuntu (KDE) on my full blown laptop and I run Lubuntu (LXDE) on my netbook.

You can install all of these on the same system without dual booting, just install the **kubuntu-desktop** package. Likewise there is a **lubuntu-desktop** package and a **xubuntu-desktop** package.

Enjoy!
~Jeff

---

### Post by murthy on 2010-06-05
Thanks, but you have missed my point.  I wanted to know if there is any difference between installing **_kde-desktop_** and installing **_kubuntu_** over ubuntu, or if they are one and the same.  I remember reading somewhere that they are different.  Kindly clarify.

---

### Post by Nythain on 2010-06-05
in the repos there's really only kubuntu-desktop, or individual kde packages like kde-core... installing kde components is much different than kubuntu-desktop, and kubuntu-desktop pretty much installs most of if not all of what gets installed with kubuntu

---

### Post by Shazzam6999 on 2010-06-05
Not entirely sure if I understand what you're asking. If you install Kubuntu on top of Ubuntu you get all the Kubuntu packages as well as all the Ubuntu packages you had previously, so it's a lot cleaner to just install a fresh Kubuntu, but otherwise there's no difference. I don't think theres a kde-desktop... as far as I know there's kubuntu-desktop kde and kde-core. Kubuntu-desktop is Kubuntu and comes with all the branding, kde is the full kde desktop and kde-core installs only the core packages (as the name suggests). Not sure what you're asking about kde/xfce.

---

### Post by XubuRoxMySox on 2010-06-05
You can put the kubuntu-desktop or xubuntu-desktop or lubuntu-desktop packages right on top of "vanilla" Ubuntu using Synaptic or using a terminal command like this example:

```
sudo apt-get install xubuntu-desktop
```

You'll have them all - but you'll need plenty of room on your hard drive. Each package downloads and installs the standard Ubuntu, Kubuntu, Xubuntu, and/or Lubuntu packages - including the default applications and configurations - to your computer.

Then you may choose one under "Session" at Login (Xfce for Xubuntu, KDE for Kubuntu, Gnome for Ubuntu, or LXDE for Lubuntu).

But wow. You'll end up with several web browsers and e-mail clients, several different file managers, utilities, etc. - Multiple installed applications for each task. It could get pretty confusing!

I suggest you try one at a time. When you're ready to try another, uninstall the one and install the next one you want to try.

Which is "better" depends entirely on what kind of hardware you have and whether you prefer simplicity, low demand on resources, a lot or a little eye candy, etc. It took me a year to choose a favorite! So take your time and enjoy the exploration.

[CENTER]Now...[/CENTER]

There are other alternatives too, besides the -desktop packages. You can install and use just a window manager (I like Openbox - it is ultralight, configurable, simple, and fast!) without any desktop environment at all. So maaaaaaany choices! That's one of the coolest things about Linux!

Enjoying the ride,
Robin

---

### Post by wojox on 2010-06-05
Its really a personal preference. What are your system specs?

---

### Post by murthy on 2010-06-06
Thanks for the replies, but I am not yet clear.  Probably I am unable to explain my doubts clearly.  The Synaptic package manager  shows both xfce4 and xubuntu-desktop.  After installing both, I get both the options (xfce and xubuntu) while logging in.  I have not studied them deep enough to know the difference and hence posted this question.  Other than this I find no particular problem with managing the multiple choices available!

---

### Post by XubuRoxMySox on 2010-06-06
> **murthy said:**
> Thanks for the replies, but I am not yet clear.  ... The Synaptic package manager  shows both xfce4 and xubuntu-desktop.  After installing both, I get both the options (xfce and xubuntu) while logging in.  I have not studied them deep enough to know the difference and hence posted this question.  Other than this I find no particular problem with managing the multiple choices available!

I'm glad you're managing them all! I don't think I could, lol. The difference between Xfce4 and xubuntu-desktop is a significant one! Xfce4 by itself is probably a little faster and alot more "ordinary," bland, kinda colorless. Xubuntu-desktop *uses* Xfce4 and configures it not only for it's simplicity, but also for balance in functionality with the most popular applications. Have a look at the [Xubuntu Strategy Document]("https://wiki.ubuntu.com/Xubuntu/StrategyDocument") for a good description of the xubuntu-desktop (otherwise known as "Xubuntu"). There's quite a bit more to xubuntu-desktop than just the xfce-4 desktop *environment*.

The exact same thing goes for KDE and kubuntu-desktop. One is just the desktop environment, while the other is a bundle of configurations and applications *using* the KDE environment. Also applies for Gnome/ubuntu-desktop, and LXDE/lubuntu-desktop.

Hoping that's clearer and helpful,
Robin

---

### Post by murthy on 2010-06-07
Thanks for the detailed reply.  Now I am much clearer about this issue.  It all depends on one's preferences, isn't it?  Thanks for all the replies and this thread may be closed.

---

