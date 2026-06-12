---
title: "Resource hunger of desktops?"
date: 2015-10-10
forum: Desktop Environments
---

### Post by Citta on 2015-10-10
Hi, 

It is said, desktop x is more resource hungry than desktop y. What is the reason and what are the consequences, when choosing a certain desktop?
Could you give me a few examples, so I can see the differences, pros and cons?

Thanks a lot for your advice!

---

### Post by alex_32 on 2015-10-10
Hi,

Unity and Gnome 3 require you to have a decent graphics cards. For example on my HP 250 G3 notebook with Intel graphics, both Unity and Gnome 3 did not run smooth. However, KDE ran very decently. 

Desktop environments like Mate, XFCE run on almost anything, but they do not have any fancy effects like KDE, Unity, Gnome and also with Mate, XFCE you might have trouble with screen tearing, and might need to install a compositor.

---

### Post by grahammechanical on 2015-10-10
If a machine has a powerful CPU and sufficient RAM and a powerful GPU, then the Desktop Environment and User Interface is a matter of personal preference. With older hardware it is a different story. Especially if the graphic adapter cannot do hardware accelerated 3D rendering. Each distribution will have a minumum hardware specification. This information can be found on the distribution's web site. The minimum hardware specification becomes relevant for machines that came with Windows XP pre-installed and machines older than that.

Regards.

---

### Post by Citta on 2015-10-11
It seems "fanciness", I assume that are eye candies, are the main reason for the need of resources? As I have nearly no experience with the mentioned DE's, I would like to know, what a certain DE is doing or not doing. Particularly in terms of getting things done as fast as possible. That does mean applications are starting and ending in a blink of an eye or real time. Finding files and other stuff easily. No need for mentioned eye candies, beauty, etc.. Is there a possibility to have a look at a certain DE, just for to get an idea what it is? I am planning to install Linux on a Thinkpad T500 with a Celeron, 2 GB RAM, perhaps replacing HDD with SSD, around 7 years old. Next one will be a PC with an i7 and SSD.

Kind regards, 
Citta

---

### Post by oldos2er on 2015-10-11
> **Citta said:**
>  Particularly in terms of getting things done as fast as possible. That does mean applications are starting and ending in a blink of an eye or real time. Finding files and other stuff easily. No need for mentioned eye candies, beauty, etc.. 

Maybe running a window manager instead of a full DE would suit this need better; most window managers are no frills, faster-than-a-DE things. 

[https://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](https://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

[https://en.wikipedia.org/wiki/X_window_manager](https://en.wikipedia.org/wiki/X_window_manager)

[http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available)

---

### Post by psychotux2 on 2015-10-12
> **Citta said:**
> It seems "fanciness", I assume that are eye candies, are the main reason for the need of resources? 
Yes, all these unnecessary gimmicks. Just to have something "new", like fashion. Planned obsolescence to make new cash.

For example, FVWM is timeless. It is still used even if it is two decades old. If you compare its features to those of a "modern" DE, you'll notice that it's much more flexible and faster than "modern" things, consumes almost no memory, and can do all these things that modern DE do.

Edit: if you need to set up a Linux box for office, mail and web, you could live well with 256MB of RAM if you use FVWM. But low resource usage is not the reason for me to use FVWM, it is its power and configurability.

---

### Post by Citta on 2015-10-12
Lots of thanks to you all for your hints! Is learning, or even study required, to get along with mentioned windows managers or FVWM, usable for beginners? Likewise when using a terminal-I tried that and I like it! Unfortunately there are so many commands to learn and to remember.

---

### Post by joe.koenig on 2015-10-12
Mr. Steve Litt gave it some thought:   [http://www.troubleshooters.com/lpm/201406/201406.htm](http://www.troubleshooters.com/lpm/201406/201406.htm)

There's even a chart:  [https://l3net.files.wordpress.com/2014/02/cmp-all4.png](https://l3net.files.wordpress.com/2014/02/cmp-all4.png)

 On a personal note, I wouldn't hesitate to use any of the BigThree (Four) KDE, GNOME, Windows8, Windows10.  My cellphone runs Windows10.  However, I love minimalistic software.  It gives me that warm fuzzy feeling that some developer has put some thought into what he/she's doing, instead of piling up humongous lines of code to get something to work.

 Doesn't work out in all instances, of course.  I.e., e,g,: I love Dillo, I use Opera and I loathe Firefox.  As always, it's a compromise.  Same with distros: Archlinux/Lubuntu + IceWM/LXDE just feels right.  Plus, I'm not missing anything from the big, bloated Big Three.  If I were, I'd be using them.

---

### Post by psychotux2 on 2015-10-12
@Joe

that article you linked to is really a nice overview of some light DMs/WMs. But I don't understand the chart. Does it show the market share or does it compare the resource usage of the various environments?

@Citta

The bad thing about FVWM is that it is made by programmers for programmers, who tend to be power users. It comes in a very basic configuration. Users configure it by editing the configuration files and possibly even adding scripts. 
Probably I'd better suggest you to use one of the WMs/DMs that are introduced in the article Joe hinted at. Maybe Lubuntu could be a good choice for your laptop.

---

### Post by joe.koenig on 2015-10-13
@psychotux2:

As to the chart, Mr. Litt simply states:
> For the rest of this magazine, I'll refer to the list of window managers, sorted by memory usage, as "netblue30's chart".

---

### Post by mcduck on 2015-10-13
It's also worth keeping in mind that a desktop environment requiring certain resources (like a decent graphics card, for example) doesn't directly mean it would be slower or heavier to run. A DE that relies on GPU acceleration would be slower if you don't have that hardware, forcing your CPU to try to do the work instead (and CPU's are pretty bad at that kind of tasks), while on the other hand if you *do* have the modern GPU around lots of the work would be offloaded to it, meaning your CPU would be left with *less* work to do, possibly even less than if you were running a simple and lightweight window manager. (Running Compiz as a standalone window manager, for example, even with plenty of eyecandy, can easily run faster and end being more lightweight than an old-school window managers without any eye candy. Assuming you have the GPU that can do the work for you, of course. The main point is offloading the work to GPU instead of your CPU, and the eye candy is just a nice bonus you can get because the GPU is so much better at that kind of work than your CPU is that doing a bit of alpha blending and drop shadows has basically no performance penalty ;))

Similar stuff applies to things like memory requirements etc, it's not just a question of what's required, but how the resources are used. A DE with higher minimum RAM requirement can very well use that memory in ways that make the DE run faster and smoother than a lighter setup would.

---

### Post by Citta on 2015-11-26
Deep insights, dense desktop fog lifted, my gratitude to all posters!

---

