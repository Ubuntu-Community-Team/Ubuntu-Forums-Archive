---
title: "WM/DE help and advice"
date: 2012-12-26
forum: Desktop Environments
---

### Post by Stafke on 2012-12-26
Hello,

I have been searching for my favorite WM/DE for quite some time now. Although I know that much is about "personal choice", I do dare to ask what you people would advise me to use.

I have been testing KDE, Gnome, Xfce, openbox (crunchbang) so it's not that this is a "I am too lazy to try for myself" question.

Besides the "personal choice" aspect, there are some issues that are needed (not all of them strictly related to the WM/DE) or desired.

* Multimonitor support would be appreciated (I highly welcome a graphical interface for this, but can even live with adding a randr script like I did in crunchbang).
* I want it to be quite good-looking (I like transparency a lot)
* automatic menu-generating is a serious plus. I dislike the fact that in openbox I need to manually modify my right-click menu for every new program I have installed.
* For my job I do need to be able to access network shares. I am not a linux expert, so manually adding/editing cifs (or what's it called) scripts is not within my knowledge.

* In fact I do not really need a DE, as I mostly install the apps I want and I consider the rest overhead (that was one of my main reasons why I have left the Redmond OS), so a pure WM is an option. Nevertheless, in that case, I do want a network-manager applet, clock, volume manager,...

An option would be any WM plus a dock (cairo dock e.g.) to launch my apps, a panel (which one?) and an application finder/launcher such as Synapse (I do like the option in Gnome Shell to just start typing and as such finding your right application)

KDE gave me too much frustration for connecting my networkshares and too many KDE apps I never use. Gnome Shell gives me not enough customization options to my liking.  Xfce did not provide me enough eyecandy (particularly transparency), while on the other hand reducing functionality to some extent. Openbox (on the minimalist side) was as such nice enough, but I got frustrated by the manual menu editing.

I know, what I want may not exist, but before deciding it doesn't I want to ask others' opinions.
Is Standalone Compiz an option? Should I stick with openbox and install Synapse + cairo dock on top of it and get used to manual menu editing? How is lxde with transparency? Does anyone have a suggestion I may not have thought of?

Thanks a lot!

---

### Post by sudodus on 2012-12-26
- How do you want to use your computer, and what are the specs?

- What about the balance between 'horse-power' and 'eye-candy'?

I have several desktop environments installed. Most of the time I run the ultra-light LXDE of lubuntu-desktop. But I have the default tools of vanilla Ubuntu, xubuntu-desktop and kubuntu-desktop, and sometimes a log into one of those environments. It is 'both and' instead of 'either or' :-)

---

### Post by Cheesemill on 2012-12-26
You don't have to manually edit your Openbox menus, there are applications that will do this for you. MenuMaker is the first that springs to mind.
As always the Arch Wiki is a great source of information:
[https://wiki.archlinux.org/index.php/Openbox](https://wiki.archlinux.org/index.php/Openbox)

Also manually editing /etc/fstab to mount your network shares really isn't difficult, there are lots of good guides about and you only need to do it the once.
[https://wiki.archlinux.org/index.php/Samba#Manual_share_mounting](https://wiki.archlinux.org/index.php/Samba#Manual_share_mounting)

---

### Post by ajgreeny on 2012-12-26
For something totally different in DE/WM territory, have a good look at enlightenment (E17) as used in Bodhi Linux 2.

It is extremely quick, very attractive, though I agree that is very personal, and most certainly worth a look.

---

### Post by Peripheral Visionary on 2012-12-26
One of the very best "newbie friendly" description of the four major desktop environments I've ever read is here:
[Linux Mint Forums • View topic - What is the difference between Debian, Fluxbox, XFCE, ...]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893")

---

### Post by Stafke on 2012-12-26
> **sudodus said:**
> - How do you want to use your computer, and what are the specs?

- What about the balance between 'horse-power' and 'eye-candy'?

I have several desktop environments installed. Most of the time I run the ultra-light LXDE of lubuntu-desktop. But I have the default tools of vanilla Ubuntu, xubuntu-desktop and kubuntu-desktop, and sometimes a log into one of those environments. It is 'both and' instead of 'either or' :-)


Thanks for your swift replies.

I use my computer both for work and leisure. Work includes office and web, of which I do a large part through a Citrix client, but also statistical software (R mainly) and some GIS (QGIS). These latter two also use my own computing power (instead of that of the server through Cirix).
Leisure includes watching movies, e-mail, surfing, some gaming.
Briefly said: no real resource intensive tasks (no 3d modelling or extensive video/photo editing)

The computer is no monster, but still fairly decent: it has a C2D E7600 @ 3GHz (x2), 4GB Ram and 150GB harddisk. I mainly use it in a dual monitor setup (one widescreen, one 'normal'). Thus, I can without problems run Gnome, KDE or whatsoever.

I find power quite important and do not like my system to use too much resources while it doesn't contribute anything. On the other hand, it is always nice to work on a good-looking system. 
To give you some examples to where I draw the line: I do not want to work on a 1990-ish gray screen and really like some transparency. Yet, I do realize that wobbling windows and cube desktop switching is nice to show off and impress other on what linux can look like (and impressing them can be nice of course), but it doesn't really contribute to my productivity (and are thus not needed). Rounded corners always please me a bit more, but as I've worked with Openbox before, I am willing to give that up if I have to :-)

The reason why I consider a pure WM instead of a full DE is because I don't like my resources wasted. It's more a philosophical thing than a practical necessity though. Why would I put my harddisk full with programs I never use? For that same reason, I feel little attracted to installing several DE's. I would rather stick with one and get the hang of it (no offence, that's just my weird mind, I completely understand your choice to use 2 or even 3).

I have briefly tested E17, but for some reason it doesn't really fit me. The setup and idea behind it seems quite different from what I'm used and I find it difficult to get around. I also have the feeling that it is good-looking, but in a way that is for me "nice-but-not-contributing". I may be wrong though.

Thanks a lot, I'm looking forward to further comments.

---

### Post by Mopar1973Man on 2012-12-26
> **sudodus said:**
> - How do you want to use your computer, and what are the specs?

- What about the balance between 'horse-power' and 'eye-candy'?

I have several desktop environments installed. Most of the time I run the ultra-light LXDE of lubuntu-desktop. But I have the default tools of vanilla Ubuntu, xubuntu-desktop and kubuntu-desktop, and sometimes a log into one of those environments. It is 'both and' instead of 'either or' :-)

I followed Sudodus for the most part. I started with vanilla Ubuntu and then loaded the LXDE Desktop. Kept most of the Ubuntu tools and pick and chose the the other tools and software I used. I wanted a light weight system with lot of CPU power but a bit of class too. LXDE has a few tweaks and tunes but a good DE to use. I personally felt the Compiz was very impressive and powerful but to complex to make it workable for daily life so I sought out a simpler DE that was light weight.

I've got just a touch of transparency basic my Conky panel on the right side of my screen. ;)

---

### Post by orange2k on 2012-12-28
> **ajgreeny said:**
> For something totally different in DE/WM territory, have a good look at enlightenment (E17) as used in Bodhi Linux 2.

It is extremely quick, very attractive, though I agree that is very personal, and most certainly worth a look.

+1 for enlightenment

I installed it a few days ago just to see how it performs and I was *amazed* to see how it:

- consumes almost no RAM (it can work with as little as 128MB)
- works on a Pentium 2 300MHz (haven't checked that because I have a newer machine
- has plenty of eyecandy
- default desktop theme is amazing

It just takes a little getting used to it - but all in all extremely recommended...

I installed Ubuntu 12.04 back and overwrote Bodhi linux just because I'm too lazy to switch now...:oops:

---

### Post by andrew.46 on 2012-12-30
> **Stafke said:**
> * automatic menu-generating is a serious plus. I dislike the fact that in openbox I need to manually modify my right-click menu for every new program I have installed.

The price of fine control is often some manual tweaking rather than the use of semi-automated tools. I run fluxbox rather than openbox but I suspect the with openbox as well there is security and *surety* in manually editing a config file. Not great speed perhaps but that is what kde/xfce/gnome are for :).

---

### Post by TeamRocket1233c on 2013-01-03
Unity, Cinnamon, GNOME Shell, or KDE should work fine on your hardware.

---

### Post by lykwydchykyn on 2013-01-03
Seems like some of your wants are a bit at odds; you want eye candy, and you want graphical tools for the things you do, but you don't want it to have extra programs you won't use.  That pretty much necessitates that someone designed a desktop for your exact use profile, which is pretty unlikely.

I think you need to decide if it's really that big of a deal to have extra stuff on the desktop that you don't use, or if you're committed enough to minimalism to dig in and learn how to work with it.

I went through a variety of DEs and WMs over the years, and eventually settled on a setup using Awesome WM (once you go tiled, you never go back) with compton doing compositing so I get transparency and whatnot.  Works awesomely with dual-monitors, very customizable and very fast.  Heck of a learning curve, though; and it doesn't have all the glitz and glitter of KDE/Unity/etc.  I just came to the conclusion that workflow was more important than looks, and went with it.

---

### Post by Stafke on 2013-01-04
> **lykwydchykyn said:**
> Seems like some of your wants are a bit at odds; you want eye candy, and you want graphical tools for the things you do, but you don't want it to have extra programs you won't use.  That pretty much necessitates that someone designed a desktop for your exact use profile, which is pretty unlikely.


That may be absolutely true and is something that I had realised a bit before, but it's good that someone pinpoints the exact problem in my thinking.

The only thing is that I do not really understand why DE developers don't stick with what they imho should: the DE. I mean, aren't most people installing firefox on top of KDE? Then why bother creating your own browser? 
Then again, I realise that my thinking does not comply with that of the devs (and most of the users), so the problem is with me.

I went to xfce for the moment, still considering Openbox or a tiling WM (seems appealing, but frightening as well).

Thanks for your advice!

---

### Post by lykwydchykyn on 2013-01-04
> **Stafke said:**
> 
The only thing is that I do not really understand why DE developers don't stick with what they imho should: the DE. I mean, aren't most people installing firefox on top of KDE? Then why bother creating your own browser? 

In all fairness, KDE doesn't describe itself as a desktop environment any more.  It's now a "Software Collection", or maybe "development community", or something.  "Plasma Workspaces" is the actual desktop environment.  But to answer the question, it's all about integrating the user experience.  Where exactly does a "DE" end?
> 
I went to xfce for the moment, still considering Openbox or a tiling WM (seems appealing, but frightening as well).


I resisted the tiling WM for a long time, and it was weird to get used to.  But once you do, you realize how much effort you used to expend managing windows.  If you code a lot, and find yourself having to reach for the mouse to resize, move, and arrange windows all the time, switching to a tiling system makes a lot of sense.

---

