---
title: "Differences between Ubuntu (GNOME),  Kubuntu and Xubuntu..."
date: 2009-05-05
forum: Desktop Environments
---

### Post by nderic77 on 2009-05-05
Is there a comprehensive thread showing the major differences, pros and cons between using GNOME, KDE and X? So far, I have stayed with GNOME, but only because it is the default and seems to be the most supported Desktop Env. What are the major differences between GNOME and the others?

---

### Post by jerrrys on 2009-05-05
[http://www.google.com/search?q=gnome+vs+kde&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=gnome+vs+kde&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by mikezila on 2009-05-05
Gnome vs. KDE is the great debate.  It's almost pure personal preference.  Gnome focuses more on being minimal and streamlined, while KDE goes full-bore with a more (no offense intended) Windows-style approach of having a whole load of options.

A more technical difference is that Gnome uses GTK and KDE uses QT.

Xubuntu uses Xfce, which is more or less intended for older or more restricted systems that have trouble running either Gnome or KDE.  There are people that prefer it, even when they can use ther others, but mostly it's used when you have a slower machine, or one with less memory.

The only real way to know which is "better" for you personally is to give them a whirl.

---

### Post by nderic77 on 2009-05-06
Thank you, Mikezila. One quick question: since KDE sounds like the more features-rich environment, does that imply that the default settings for KDE would tend to be more resource-intensive than for GNOME?

nb: when I have time, I plan to reinstall with 64-bit Jaunty, replacing my 32-bit Intrepid system with EXT4 partitions. Initially, will dual-boot 64 and 32 bit variations; hopefully I will be comfortable enough w/ 64 to drop the 32 bit install. I am debating either going with GNOME or KDE for the new install. Prefer not to go too resource-intensive since i run a pretty resource-hogging XP guest on VMWare Server.

---

### Post by mikezila on 2009-05-06
> **nderic77 said:**
> Thank you, Mikezila. One quick question: since KDE sounds like the more features-rich environment, does that imply that the default settings for KDE would tend to be more resource-intensive than for GNOME?

Not necessarily.  On a modern computer the difference in performance will probably be imperceptible.

What I would do if you're curious about this, is just install Kubuntu and try it, and if you don't like it, just wipe it out in favor of Ubuntu.  You're already experimenting at this point, and it's best (and safer) to give it a try now than after you've got everything setup like you want it.

---

### Post by spillin_dylan on 2009-05-06
You can actually have them both installed at the same time, too.  

```

sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop

```

From the login screen there will be a "Select Session" option where you can choose which X session you would like.  There are many other window manager & desktop environments to choose from, too, and all can be installed and chosen in this manner.

---

### Post by 37fleetwood on 2009-05-07
> **spillin_dylan said:**
> You can actually have them both installed at the same time, too.  

```

sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop

```

From the login screen there will be a "Select Session" option where you can choose which X session you would like.  There are many other window manager & desktop environments to choose from, too, and all can be installed and chosen in this manner.

silly question, what are the chances that this will cause unforseen problems?
my system is working pretty well and I'd hate to mess it up playing around. also will these install through apt?
thanks and sorry for the detour.

---

### Post by joewski on 2009-05-07
> **37fleetwood said:**
> silly question, what are the chances that this will cause unforseen problems?


The only problem you will have is if you create a new user and you want to have a certain type of desktop. I am asking the question in another thread at the moment.

However you can try different desktops and in between trying a new desktop create a new user. I used desktop1 desktop2 etc for each desktop. By logging into each after installation the new user is given the new desktop layout. It a great way to fell a a desktop is going to fell like natural so to speak.

---

### Post by 37fleetwood on 2009-05-29
Ok, I installed Ubuntu 9.04 and installed the Kubuntu desktop and the Xubuntu desktop. can the OpenGeu be installed in a similar manner? what would the terminal command look like? are there any others that can be this easily installed? space is not a problem as I'm installed on a 500 gig drive with 400 gig free:)
thanks
Scott

---

