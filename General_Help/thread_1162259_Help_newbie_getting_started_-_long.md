---
title: "Help newbie getting started - long"
date: 2009-05-17
forum: General Help
---

### Post by tpx60s on 2009-05-17
Hi
I currently run XP pro on my Thinkpad X60s and would like to migrate to Ubuntu. I've installed Ubuntu on VMWare through XP to have a little play to get a feel of how it works. I now have a few answers to help get me started.

What's the best way to migrate to Ubuntu? Should I create a new partition on my HDD and install Ubuntu there and once everything is configured and working, remove the XP partition? I don't think I'll need to have dual booting with XP once Ubuntu is fully working and configured.

Everything I've read so far indicates that Linux's power management isn't very efficient and you don't seem to be able to achieve the same sort of battery life as you can with XP. I'm frequently away from a power source so will require to be able to achieve similar battery life under Ubuntu as I am in XP. Is this possible?

Will all the Thinkpad specific functions be supported under Ubuntu? I'm talking about things like the fingerprint reader, the browser back and forward buttons, screen brightness buttons, sleep / hibernate buttons, wifi enable / disable, external screen selector buttons, volume control buttons, etc. Is there a specific Thinkpad module to install for these?

I also notice that with my installation of Ubuntu over VMware, that the processor often maxes out even when performing what is a trivial task like opening a window or dragging a window (I don't have any of the fancy eye candy or effects enabled). I'm not sure how much of this is due to VMware and the shared resources but under battery power it sure drains the battery. 

So far for the day I've been playing with Ubuntu it's a massive learning curve, especially with a lot of the command line stuff you need to do to get things to work or installed. Is this typical of Linux?

Lastly, is it better to use drivers, etc packaged specifically for Ubuntu(if they exist) than download and use the ones that the manufacturers release, e.g. Intel video drivers, etc?

I look forward to the responses and getting started. :D

---

### Post by snowpine on 2009-05-17
Welcome to the forums! I would start by skimming through this thread, which is chock-full of information: [http://ubuntuforums.org/showthread.php?t=645208](http://ubuntuforums.org/showthread.php?t=645208)

(Hint: use the "search this thread" feature to find x60s specific info)

I am not personally a thinkpad owner, so I can't give you much specific advice, just point you in the right direction. The best advice I can give is to simply burn a Live CD of Ubuntu and try it with no change to your computer. That will quickly answer your questions about which hardware features work and which don't out-of-the-box. 

ps VMware is not a good gauge of performance, because you are running Ubuntu on top of Windows.

---

### Post by Shpongle on 2009-05-17
Hey welcome to the forum:D,you  may wanna take a look at this [http://benzipperer.info/installing-ubuntu-feisty-7-04-thinkpad-x60s](http://benzipperer.info/installing-ubuntu-feisty-7-04-thinkpad-x60s) ,

for me most of the stuff worked out of the box and support  for newer makes and models is constantly being added and updated, i found i got much more out of my system after switching from windows, the power management was better under ubuntu!!!, if you do switch you'll soon realize how efficient linux is, id recommend you try running a live cd , and see how it runs and it will give you a good indication of what will work!,

also most problems can be simply fixed and support is always available here at the forums, id recommend duel boot to begin with , just to be safe and you can always delete the windows partition later if you wish!, as far as the command line goes most of the time you will just be copy & pasting  also theres loads of free online references for all that stuff,  

hope this helps:D

---

### Post by irv on 2009-05-17
Before answering your questions I would make a suggestion. Before installing Ubuntu I would boot with the live CD and run the OS off the CD and then check out your performance and make sure everything is working like your wifi, Internet, your keys on your keyboard etc. (Don't forget it will run slower off the CD then the Hard Drive).After you do this come back and post what is working and what is not. From there others can help you get going. Also list your hardware, how much memory you have, video etc.
I have Ubuntu on my old laptop and the battery is getting bad so my battery life is not good anymore but it was great at one time. I thought it was better then XP and faster. I have a new laptop with Vista and my old laptop seems to run faster that the new one.
I hope you can get Ubuntu to work the way you want because it is much better then Windows in my opinion.

---

### Post by tpx60s on 2009-05-18
Thanks for the replies. I'll do as suggested and check how things run with the live CD. I am hopeful that I can get it working as I wish and that the power mangement is at least on par with XP.

---

### Post by Sef on 2009-05-18
Read [Psychocats]("http://psychocats.net/ubuntu").

---

### Post by 3rdalbum on 2009-05-18
> **tpx60s said:**
> Thanks for the replies. I'll do as suggested and check how things run with the live CD. I am hopeful that I can get it working as I wish and that the power mangement is at least on par with XP.

Power Management is where the screen dims when you take out the power plug, you can suspend and hibernate etc. On that score, Linux is as good as or better than Windows.

What you're talking about is resource use. Windows XP was made in 2001, so it's a little bit odd to compare its resource use to the latest version of Ubuntu. If you want absolute maximum battery life you should try Windows 3.1 as it was designed to use much less system resources than Windows XP. Or better yet, MS-DOS or FreeDOS.

Under the latest Ubuntu, you'll probably get 2/3 or more battery life than under XP. I'd be more inclined to say "more than 2/3". If you run anti-virus on XP then you could well have better battery life under Ubuntu than under XP, as Ubuntu won't be pushing the HDD and CPU as much.

There are things you can do to increase power efficiency over and above Ubuntu's default settings; for new users I recommend installing Intel's Powertop software, it's available in the Synaptic Package Manager. You run it in a terminal window like this:

```
sudo powertop
```

It shows what programs are using the most battery power, how many times your CPU gets woken up from powersaving mode per second, and it also suggests settings to apply that will decrease power use.

If you're really pro, you can look at the suggestions on [www.lesswatts.org](www.lesswatts.org), but those are generally more invasive to apply or have already been rolled into the default Ubuntu.

Good luck.

---

### Post by CatKiller on 2009-05-18
> **tpx60s said:**
> So far for the day I've been playing with Ubuntu it's a massive learning curve, especially with a lot of the command line stuff you need to do to get things to work or installed. Is this typical of Linux?

It's typical of the forums.

Given that this forum is text-based, the graphical environment is hugely customisable, and people here might be running Gnome, KDE, Xfce, or something else, giving instructions along the lines of "click on this orange thing, then that blue thing, then something else..." is both ambiguous and time-consuming. A simple, clear command that can easily be copy-and-pasted into the Terminal is much more efficient. Plus, running a command in the Terminal gives you feedback that you don't necessarily get when using the graphical tools directly.

The command line is a very powerful and flexible tool, but you don't need to use it day-to-day unless you find that it's the best tool for the job for what you want to achieve and the way that you prefer to work. When I use the command line it's because it's the quickest way to do what I want.

---

### Post by tpx60s on 2009-05-18
Yes, you're correct, I was referring to resource use. I used the wrong terminology.

My concerns were brought up due to the reading on various forums (generally about Linux) I've been doing. actually i've read some many different topics on forums it's all becoming a bit of a blur. One of the issues for example was where there have been observations that the power to HDDs are not managed as well in Ubunu / Linux as in XP, i.e. they don't spin down after some time. I am still new to Linux so I cannot really say if these problems are general across the board or specific to one person's set up.

I guess I'll just have to try it.

---

### Post by tpx60s on 2009-05-18
> **CatKiller said:**
> It's typical of the forums.

Given that this forum is text-based, the graphical environment is hugely customisable, and people here might be running Gnome, KDE, Xfce, or something else, giving instructions along the lines of "click on this orange thing, then that blue thing, then something else..." is both ambiguous and time-consuming. A simple, clear command that can easily be copy-and-pasted into the Terminal is much more efficient. Plus, running a command in the Terminal gives you feedback that you don't necessarily get when using the graphical tools directly.

The command line is a very powerful and flexible tool, but you don't need to use it day-to-day unless you find that it's the best tool for the job for what you want to achieve and the way that you prefer to work. When I use the command line it's because it's the quickest way to do what I want.

That makes complete sense and I didn't look at it that way. I was once used to command line stuff in the old days of DOS but with years of windows have got lazy. I'll need to read up on some of the more common Linux commands.

---

### Post by irv on 2009-05-18
> **tpx60s said:**
> That makes complete sense and I didn't look at it that way. I was once used to command line stuff in the old days of DOS but with years of windows have got lazy. I'll need to read up on some of the more common Linux commands.
Here is a link to one you might find useful. Also just do a search on "Linux Command Reference" and you will find many more.
[http://3.bp.blogspot.com/_jRRL0p_4W9I/SCqUmxZvu3I/AAAAAAAAAdY/-JBQu1mdh-s/s1600-h/ubunturef.png]("http://3.bp.blogspot.com/_jRRL0p_4W9I/SCqUmxZvu3I/AAAAAAAAAdY/-JBQu1mdh-s/s1600-h/ubunturef.png")

---

