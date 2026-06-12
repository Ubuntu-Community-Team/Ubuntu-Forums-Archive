---
title: "Going back to Gnome 2"
date: 2011-11-17
forum: Desktop Environments
---

### Post by Trilby on 2011-11-17
I've been using an fresh install of Ubuntu 11.10 for a few weeks now. I can't get on with Unity, so I've been using Gnome Shell for the most part. I find Shell ok, at the very least, better than Unity, but honestly, it's tiring. I've been trying out KDE bit too and kinda like it but in truth, I miss Gnome 2. I'm about to install Ubuntu on another PC of mine and really want to go back to the way I used to have my desktop. I'd customised until it was just as I wanted it.

In short, how do I install Gnome 2 (with Compiz) on Ubuntu 11.10? I hope this isn't a silly question.

Much thanks for any help,
Trilby.

---

### Post by cbowman57 on 2011-11-17
Closest you're likely to get is Mint 12 with the Mate desktop.

---

### Post by Copper Bezel on 2011-11-17
There's something called the MATE desktop that will allow you to install the Gnome 2 environment on a current system. It's in progress at the moment, however. You could use the Gnome Fallback session and run Compiz over that, or use some of the Gnome Shell extensions (such as _[this pack]("http://intgat.tigress.co.uk/rmy/extensions/index.html")_) to make Shell work a bit more like the classic interface.  They're all sort of stopgap measures, though - Gnome 2 and Gnome 3 aren't separate projects, so Gnome 3 is simply the current version of the Gnome desktop. If you've put a lot of effort into customizing something to your preferences, that can be frustrating, but the options are bound to change over time, so you have to assume that those kinds of tweaks aren't always going to work or be relevant.

---

### Post by 3Miro on 2011-11-17
11.10 has something called Gnome-classic or Gnome-fallback, this is close to Gnome 2. The Mate project is still not available for Ubuntu and I don't know the general state of this.

If you insist on Gnome 2, your best options are either Ubuntu 10.04 or Debian 6. Those have support for another 2 and 3 years respectively.

KDE is a good DE, but it is quite a bit different form Gnome 2. You should try XFCE, it usually takes a bit more to setup, but in many ways I find it better then Gnome 2.

---

### Post by tartalo on 2011-11-17
This has been discussed a lot, but it was all a huge chaos. Your best options are:

- Force yourself to like Unity (Some people say that they didn't like at the beginning but got used, no reason to believe they lie)

- Install gnome-session-fallback (similar to Gnome 2, but not the same, some find it good enough)

- Change the Desktop environment (KDE, XFCE and LXDE are mentioned most often, seems to be a popular option)

- Install an earlier version of Ubuntu (10.04 LTS is the logic option, apparently a popular choice too)

- Switch to Debian Stable (Gnome 2 will be supported for a couple of years, beware of hardware support)

- Switch to Mint (They adapted Gnome 3 and incorporated MATE, a fork of Gnome 2. there are high hopes about the outcome but it's still unreleased)

---

### Post by Copper Bezel on 2011-11-17
No, he already tried the *best* option, with Shell. = ) But I'd assume he's aware of most of those things.

I can't *believe* I'm the one saying this, but XFCE, specifically, has been much lauded of late for being extremely Gnome-2-like, and it might suit your purposes, depending on what you need out of your DE, to start with that (+ Compiz.)

Edit: Oh, and make Nautilus a startup application, so that it'll draw the desktop, which it will do every time you run it under XFCE anyway, whether you want it to or not. = P (Barring some tweaking in dconf or Gnome Tweak Tool.)

---

### Post by cbowman57 on 2011-11-17
> **Copper Bezel said:**
> No, he already tried the *best* option, with Shell. = ) But I'd assume he's aware of most of those things.

:lol:  I was trying to answer him without bias, but you're right about gnome shell. :)

---

### Post by tartalo on 2011-11-17
Yes, I forgot Gnome Shell.

I don't understand why there's no sticky answering this question yet.

---

### Post by 3Miro on 2011-11-17
> **Copper Bezel said:**
> 
Edit: Oh, and make Nautilus a startup application, so that it'll draw the desktop, which it will do every time you run it under XFCE anyway, whether you want it to or not. = P (Barring some tweaking in dconf or Gnome Tweak Tool.)

Or you may just disable xfdesktop and use Nautilus instead of Thunar. Many people prefer Nautilus because it has couple of extra plugins. I personally prefer the speed of Thunar.

If you take a xfce distribution (i.e. xubuntu), then there would be much fewer things to set. However, just adding it to Ubuntu will require a few tweaks (as I mentioned earlier).

---

### Post by 3Miro on 2011-11-17
> **tartalo said:**
> Yes, I forgot Gnome Shell.

I don't understand why there's no sticky answering this question yet.

He is using Gnome-shell right now, hence I didn't mention it.

You are right that there should be sticky written by someone who lists all the options preferably written without interjecting opinion (including the horrible Gnome-shell).

---

### Post by Copper Bezel on 2011-11-17
Yeah, maybe, although the topic honestly comes up far more in Café than here in Desktop Environments. If you mean to list pro-and-con features for each, you'd probably need some collaboration, because no one is really equally versed in all of them and, as you say, there's going to be bias. For instance, I think you'd write a more useful description of XFCE and I'd write a more useful one for Gnome Shell, as opposed to the reverse. = )

Edit: The idea being, rather than trying to artificially remove bias and end up confusing matters further, just give each one an equal amount of "pitch."

---

### Post by 3Miro on 2011-11-17
> **Copper Bezel said:**
> Yeah, maybe, although the topic honestly comes up far more in Café than here in Desktop Environments. If you mean to list pro-and-con features for each, you'd probably need some collaboration, because no one is really equally versed in all of them and, as you say, there's going to be bias. For instance, I think you'd write a more useful description of XFCE and I'd write a more useful one for Gnome Shell, as opposed to the reverse. = )

Well, I am XFCE user since Ubuntu 9.10, so it is expected that I will know it better. We can have users of each DE write a short description or we can just list the options with little information. However, regardless of what you write, people cannot makeup their mind without actually trying the DE. Before I settled on XFCE I did have Gnome 2, KDE, LXDE and XFCE all installed. I have also spend time with both Unity and Gnome-shell, although I am not as familiar with those two.

---

### Post by Copper Bezel on 2011-11-17
Yeah, that's pretty much what I'm getting at. But there's also the fact that every desktop has its own Zen - you can't go into Unity expecting the top panel to work like an XFCE panel, or go into Gnome Shell or XFCE and expect the Favorites bar or the launcher panel, respectively, to perform the same roles as the Unity Launcher, without ending up very disappointed. 

There's a certain extent to which the DE is just either going to fit or fail to do so. Of course the user is going to need to try any DE before settling in, and some decisions are going to be easier than others. It took me about an hour to decide against Unity and somewhere between two days and a week of use to decide against XFCE. 

But the user does have to adapt to the DE a little, too, and I think it would be useful to have perspectives from daily users that give a little bit of a sense of how the DE is intended to be used, let the DE get its best showing in that test run we're talking about. (My abject horror on seeing Shell the first time and realizing that keyboard navigation was simply *nonexistent* outstripped *anything* I experienced in Unity or XFCE, for instance. = D )

---

### Post by Anastasis on 2011-11-18
My Mate desktop environment upgrade. It's...it's just a beautiful thing, man.

BUAAASHAHAHAHAHAAHAHAHAHAHAHAHAAA AAA!

AHHAHAHA

HAAAA!

[IMG]http://i947.photobucket.com/albums/ad313/Archangelos2010/mate-desktop.png[/IMG]

---

### Post by VanillaMozilla on 2011-11-18
Yes, that's nice, Anastasis.  Now, how do I get that to look like and work like Gnome 2 under Ubuntu or Fedora?  Thanks to Gnome 2, I finally have a clean desktop.  And the three menus at the top classified everything nicely so you could find stuff easily (without rummaging around underneath windows), among other advantages.

---

