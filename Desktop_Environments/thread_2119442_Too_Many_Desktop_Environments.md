---
title: "Too Many Desktop Environments?"
date: 2013-02-23
forum: Desktop Environments
---

### Post by Bouvet on 2013-02-23
Hello Forum,
My question is, "Can you have too many desktops?"
I have installed Ubuntu 12.04 (Unity) and I am running 
two more: Cinnamon (Gnome Classic?) and Mate. I've been curious
to try XFCE and a few others, but I was worried that
too many desktops would compromise my system.
I am running 8MB on a 120GB SSD in a laptop. 
Any advice would be appreciated. Thank you.

---

### Post by QIII on 2013-02-23
The only problems you would have are a bit of extra disk space used for applications and dependencies as well as a few extra applications showing up in launchers.

When you select a DE, you are running only that one, so you are not using memory or processor time to run the others.

If space is at a premium, there are ways to remove some DE's (Psychocat's tutorials) but even as good as the methods are you take some risk of borking.

---

### Post by Bouvet on 2013-02-23
Thanks for the quick tip QIII.
I gave my specs in my first posting and I don't have anything stored
on my HD, I have it all on Ubuntu One. So you're saying it is ok to 
install more desktops? I would really like having more to chose from.

---

### Post by zombifier25 on 2013-02-23
Yes. You can install as much as your hard drive allows. In fact, most people here probably has 4+ DEs and WMs installed.

---

### Post by Bucky Ball on 2013-02-23
Go for it. You are only using one at a time. When you've settled on what works best for you, you might think of reinstalling a customised system with your favourite desktop environment. Basically what I did but it took a few years to get there!

Play around and enjoy the exploration. ;)

---

### Post by Bouvet on 2013-02-23
THANKS everyone, my gut feeling told me it was ok, but I asked one
person online and he told me that a person can have too many and it
might wreck the system. I thought I installed Cinnamon, but it isn't 
showing up. That's one I want to try as well as a few others. I saw
a thread on site here about installing desktops and will follow it.
You all have been a great help. I'm excited now. :)

---

### Post by deadflowr on 2013-02-23
The problem with too many desktops, for Ubuntu at least, besides disk space, is lightdm can only show you so many before they drop off the screen.
The easy solution is to switch display managers and use gdm:
```
sudo dpkg-reconfigure lightdm
```
and choose gdm. From then on you'll boot into the gdm login screen. Though you will lose the wallpaper per user session nifty display.

---

### Post by Bouvet on 2013-02-23
Ohh, glad I checked back here D.Flower.
THAT might explain why I cannot see Cinnamon desktop
that I know I installed, and even used. I thought it
'fell off'. I'm going to look into gdm ( never heard of
it till now) and if I have to, I will pay the price
of wallpaper. Great tip!

---

### Post by Bucky Ball on 2013-02-24
I think there's a bit of confusion here because of the title of the thread. You actually mean too many desktop environments rather than desktops. I'll change the title to reflect this. ;)

---

### Post by tartalo on 2013-02-24
I find more convenient using a virtual machine to try different desktops or distros.

---

### Post by uc50_ic4more on 2013-02-24
All of the DE's you mentioned hypothetically are GTK-based. There ought not to be too terribly much in the way of "wasted" disk space. Heck, you may be able to maintain one GTK theme throughout all of those DE's. Greybird comes to mind as a GTK theme that may well look and feel alarmingly similar across Unity, "straight" Gnome, XFCE, LXDE, Mate and Cinnamon!

---

### Post by Bouvet on 2013-02-26
> **Bucky Ball said:**
> I think there's a bit of confusion here because of the title of the thread. You actually mean too many desktop environments rather than desktops. I'll change the title to reflect this. ;)

Oops, I didn't realize there was a difference in wording. Sorry.
Yes, I meant 'environments'. I was told by someone else that
too many 'environments' is bad and harmful. After reading this
thread, I think he was greatly mistaken as I was in my wording. :)

---

### Post by Bouvet on 2013-02-26
> **uc50_ic4more said:**
> All of the DE's you mentioned hypothetically are GTK-based. There ought not to be too terribly much in the way of "wasted" disk space. Heck, you may be able to maintain one GTK theme throughout all of those DE's. Greybird comes to mind as a GTK theme that may well look and feel alarmingly similar across Unity, "straight" Gnome, XFCE, LXDE, Mate and Cinnamon!

Good to know. I didn't want to put too many 'environments' on
and have it slow my system down. I think I'll stay with the three
that I have and stop while I'm ahead. :P

---

### Post by uc50_ic4more on 2013-02-26
> **Bouvet said:**
> Good to know. I didn't want to put too many 'environments' on
and have it slow my system down. I think I'll stay with the three
that I have and stop while I'm ahead. :P

Remember that you'd only be running one DE at a time; so having multiple DE's installed - especially when they're all so closely related in terms of the graphical toolkits used to build and display them, means that at worst you're going to have some redundancy in the applications you have. One DE may use an application to view images and another DE may use another. But given that you can set these defaults independently of the DE with which each application is associated, this actually avails you with more choices!

When I used Arch as my primary OS, my cobbled-together customized DE was a combination of XFCE and LXDE components.

---

### Post by Bouvet on 2013-03-01
Yes UC50, I'm finding out that the more DE I have, the more updating I have to do when I use them . I'll keep the three I'm running, but I have a gut feeling eventually I'll remove one and just have two.
Of course after admitting that, I have no idea how to remove them! LOL. I'll have to poke around this site and I'm sure there's a link or two. Thanks for stopping by to leave your remarks.

---

### Post by VanillaMozilla on 2013-03-01
The desktops are not really well separated.  You will litter your menus with elements of more than one desktop, and you probably won't know which programs belong to which.  Each desktop will also change some defaults, and you will have no idea how to change them back.  So it's a little messy, but it probably won't break anything.

P.S.  Cinnamon is not Gnome Classic.  To get that, install the gnome-fallback-session package.  That one really doesn't seem to clutter your system much.

One problem I had with adding desktops is that the logon manager may break.  You can stll log on, but you may not have a choice of sessions.  That problem is allegedly fixed, except when it isn't.

---

