---
title: "Ubuntu with Xubuntu-Desktop vs. Xubuntu"
date: 2009-05-14
forum: Desktop Environments
---

### Post by javyn999 on 2009-05-14
Hey all.  I've got an Acer Travelmate laptop (291Lmi) with the following specs:

1.3 ghz Intel Mobile processor
512 RAM
Integrated video card, video is handled by processor and ram.
Ubuntu Jaunty Jackalope 9.04 installed

Jaunty runs great on it, but of course, I think my lack of video card is a limiting factor as far as speed and responsiveness goes.  I installed the Xubuntu-Desktop on my desktop computer running Jaunty, and really like it.  I'd like to put it on my laptop.

My question is...would I be better off doing a clean install of Xubuntu as far as speed goes?  Or will it be the same as running Ubuntu with the Xubuntu-Desktop installed?  I ask because of course, I'd like to avoid a clean install of Xubuntu, but I will do it if there is a noticeable speed difference.  

Any opinions would be appreciated!

---

### Post by kerry_s on 2009-05-14
i'd go for a clean install, start fresh, only the bloat that already comes with it.

but if you want just install xfce4 instead of xubuntu-desktop, basically the same thing, but with out the xubuntu bloat.

---

### Post by appier on 2009-05-15
I did a clean install of Xubuntu on an older Gateway that has an 800 Mhz processor with 256 MB of RAM.  It is running fine, and is very snappy when compared to the XP it replaced on the same machine.  My recommendation would be to go with a fresh install, but it should run fine either way with the specs you quoted for your computer.

---

### Post by javyn999 on 2009-05-15
Tried just installing the xfce4 desktop, ugh, it has no sound or volume controls...what am I missing here?  

I'll give Xubuntu a shot when Koala comes around I think.  Since the laptop has integrated video, I think Gnome would be pointless.

---

### Post by gjoellee on 2009-05-15
> **javyn999 said:**
> Tried just installing the xfce4 desktop, ugh, it has no sound or volume controls...what am I missing here?  

You need to add the volume contorl to the panel! (It is called "Mixer"). You can also start the mixer from terminal:
```
xfce4-mixer
```

---

### Post by utnubuuser on 2009-05-15
Maybe have a look at #!CRashbang Linux

---

### Post by javyn999 on 2009-05-18
Thanks guys.  I'll give xfce4-mixer a go.  

I installed Slackware 12 into a Virtualbox Saturday night, and have to say I'm amazed with its speed!  Eventually I'd like to move over to Slackware, but I'm such a Linux newb, I don't think I'm ready yet.  I'll just play around on it in my Virtualbox.  Still....I had 0 issue installing it and Slack is supposed to be the hardest to install and set up, so maybe I'm not too far off!

---

### Post by snowpine on 2009-05-18
xubuntu-desktop is exactly the same as a fresh install of Xubuntu. You would see no improvement in speed if you reinstall.

If fast performance is your number one priority, I highly recommend leaving Ubuntu (and its derivatives such as Xubuntu) behind. Ubuntu is arguably the easiest to use, fullest featured Linux disto available, which necessarily makes it one of the "heavier" distros. Here is some interesting reading material: [http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)

---

### Post by XubuRoxMySox on 2009-05-18
> **utnubuuser said:**
> Maybe have a look at #!CRashbang Linux

LOL, that's [Crunchbang]("http://crunchbanglinux.org"), not crashbang. I'd be scared of an OS that had the word "crash" in it's name!

I use Crunchbang on an ancient old 'puter that my family gave up for dead years ago, and it flies along, speedy and lightweight. Sweet!

But I'm still a newbie who needs the familiarity and simplicity of a "Windowsy" desktop, so I put the uber-lightweight [LXDE]("http://lxde.org") on top of Crunchbang for a pretty, simple desktop with icons and all that newbie-friendly stuff I need (and prefer).

Using the built-in file manager PCMan, applications appear as icons in /usr/share/applications. Just drag the ones you want and drop them on your desktop!

Wicked-kewl wallpapers can be placed in /usr/share/lxde/wallpapers and selected from Edit > Preferences in PCMan.

It's beautiful, functional, uber-newbie friendly, and ultra lightweight. My customized Crunchbang runs at mind-bending speed even on that old run-down 'puter. LXDE is *extremely* lightweight and newbie-friendly!

-Robin

---

### Post by utnubuuser on 2009-05-20
LOL.  Thanks.  Good Catch!  I meant CrunchBang.

---

