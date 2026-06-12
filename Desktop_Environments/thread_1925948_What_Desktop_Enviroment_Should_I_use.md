---
title: "What Desktop Enviroment Should I use?"
date: 2012-02-15
forum: Desktop Environments
---

### Post by Serpher on 2012-02-15
So I've been a fan of GNOME 2 for quite a while, however after trying pretty hard to take a liking to GNOME 3 in distros such as Fedora 16, it's not for me. I'm not trying to start a holy war or anything but it just isn't suited to my type of work nor is the Unity environment. I was wondering what desktop environment you guys could suggest that is going to stay up to date for a fairly long period of time, and not go down the same OSXish path of GNOME 3 and Unity.

I've used LXDE, XFCE, and KDE before but honestly none of them did it for me like GNOME 2 did and in a few years I'm scared of running into problems with GNOME 2 being left behind. KDE seems bulky, XFCE seems kinda gimped, and LXDE feels like it should only be used on a low power machine. I'm learning towards KDE but what do you guys think? Would spending the time on making a proper OpenBox environment be worth it?

---

### Post by jerrrys on 2012-02-15
What about gnome classic.  Its not an exact match to gnome2, but workable.

sudo apt-get install gnome-session-fallback

---

### Post by Simian Man on 2012-02-15
Each release of KDE is better, faster and more streamlined than the previous version.  I think if you gave it a fair shake, you'll forget all about Gnome 2.

---

### Post by haqking on 2012-02-15
KDE 4.8 on my recent slackware 13.37-current build works like my machine is on rocket fuel.

Saying that it is on a SSD and 16GB ram with i7, everything happens before i even decide to start it ;-)

---

### Post by lykwydchykyn on 2012-02-15
It really depends on what you want balanced by what your hardware can take.

My work desktop is pretty powerful and new, so I run KDE on it.  It *is* bulky by comparison, but I never want for tools or features, and it looks great.

On my laptop I've used about everything: KDE, XFCE, LXDE, various customized openbox setups, icewm, etc.  I'm currently using awesome.

In my experience, XFCE is rock solid, dependable, has just about everything you'd expect a desktop environment to have, but on the downside it's not very exciting or modern looking.

If you go the openbox route (or building  a DE from any standalone WM), IME the desktop setup becomes a never-ending work-in-progress, and you'll find yourself having to reinvent the wheel on stuff that's just a click or two on the average DE.  If you're weird like me and actually enjoy that challenge (and not afraid of the command line), go for it.  You'll reap the reward in speed, if nothing else.

---

### Post by cortman on 2012-02-15
Honest inquiries are always welcome!
Normally I would say XFCE, as it gives the classic experience and gives you the added benefit of being more lightweight and streamlined. It's not the prettiest out there, but a little tweaking can go a long way.
If the Cinnamon project gets stabilized, I think there's a lot of potential there. It's a re-working of Gnome Shell, so you get all the Gnome good looks and themes and yet have a Gnome2-esque experience. I'd say its success depends a lot on the availability of panel widgets and other panel options.
KDE is a matter of taste; I can see good things about it, but I'm a Gnome man. If your machine can handle it, KDE will give you all the smoothness and good looks you want.

---

### Post by Rafterman414 on 2012-02-15
Lately I have been trying to give Unity a shot but I usually find my self using KDE on my desktop and XFCE on my laptop. I like the familiar layout of both KDE and XFCE and the intuitive design which fits into my workflow nicely. If you are looking for something very lightweight LXDE is a great choice which also delivers a familiar look and feel.

---

### Post by josephmills on 2012-02-15
there are tons window managers out there 
here are some that I thought that I would throw in the mix 
Fluxbox 
[http://fluxbox.org/](http://fluxbox.org/)

openbox 
[http://openbox.org/](http://openbox.org/)

sawfish 
[http://sawfish.wikia.com/wiki/Main_Page](http://sawfish.wikia.com/wiki/Main_Page)

blackbox 
[http://blackboxwm.sourceforge.net/](http://blackboxwm.sourceforge.net/)

KDE4.8 

FVwM 
[http://www.fvwm.org/](http://www.fvwm.org/)

IceWm 
[http://www.icewm.org/](http://www.icewm.org/)

enlightenment 
[http://www.enlightenment.org/](http://www.enlightenment.org/) 

afterstep
[http://cmdrtaco.net/linux/afterstep.shtml](http://cmdrtaco.net/linux/afterstep.shtml)

Hope that this helps in some sorta way

---

### Post by Serpher on 2012-02-15
Thanks everybody. I think I'm starting to learn towards XFCE since it uses the GTK+ library which is what most of my preferred applications run on and use. It also has more of a GNOME feel to it. I think I'm going to switch over to Linux Mint for my work computer. Thanks everybody! I'll still be active in this thread if people still want to throw a couple more things at me.

---

### Post by winh8r on 2012-02-15
I found this:

[http://mate-desktop.org/]("http://mate-desktop.org/")

to be exactly what I wanted and needed in a desktop environment on 11.10.

But as they say, try them out and use whatever works for you the best in your situation.

hope this is of some use to you.

---

### Post by LewisTM on 2012-02-15
XFCE is a wise choice. The next version should be even better.
To give it a more modern look, just throw in Cairo-dock.
You'll get a cool 3D dock, versatile launchers and plugins and even some nice desklets.
Synapse can give you the search-and-launch capability of other DEs. Compiz/Emerald also work nicely in XFCE if you want even more visual magic.

Cheers!

---

### Post by NerdWermz on 2012-02-15
I went to XFCE from Gnome and I love it.    

To me Gigolo is a little unwieldy, having to input username and password twice for each share rather than just once, but I am use to it now.

---

### Post by llanitedave on 2012-02-15
It really is nice to have so many choices!

I've tried Unity, KDE, Xfce, and Lxde, and I took a quick look at Gnome3.

There's a lot I like about KDE, but it does seem a bit "busy", and unfortunately is fragile on my system.  I hear there will be some improvements on 4.8, and I'll be willing to try them.

There's a lot I like about Xfce and Lxde, in fact I can't find anything specifically to complain about with either one of them.  Lx is simple and basic, and not as configurable as the others, but it's still quite attractive, supports all the tasks I need it to, and looks really clean and well designed to me.  

But for some reason I keep drifting back to Unity.  It's not perfect, but it does seem to utilize screen space better, and I developed an intuition for it fairly quickly.

---

### Post by andrew.46 on 2012-02-16
Perhaps also be aware that there is a difference between a *window manager* and a *desktop enviroment* :). My personal vote goes to a great window manager: Fluxbox. Well worth the little bit of research required to get it all running smoothly...

---

### Post by xadder on 2012-02-16
I also struggled with unity but eventually decided it was too much hassle. Have now settled into xfce, which makes life much easier. Added synapse recently as recommended in another post, and I have loads of fast ways of accessing menus and commands. Pretty happy now.

---

### Post by absolutezero1287 on 2012-02-16
Try and decide what it is that you REALLY need? Are you looking for something lightweight and speedy? If so then you may want to look at more minimalist setups with window managers like fluxbox, openbox, xmonad, and awesome. I prefer fluxbox for these kinds of setups. Keep in mind that setting up your environment will take a while and you might not be completely satisfied.

---

### Post by tuggy on 2012-02-17
My .02 here:

After being bored with Unity and gnome-shell (yes, I'm a die-hard gnome2 fan), I tried a few other options for a while, namely Enlightenment, XFCe and WindowMaker.

I'm now a proud WindowMaker user :D
It needs a bit of tweaking, and you wont find very modern look/feature in it, but it rocks my world at the moment :)

and here is a screenshot of my writing this post :popcorn:

[http://imgur.com/AxwEw](http://imgur.com/AxwEw)

cheers!

---

### Post by markbl on 2012-02-17
> **xadder said:**
> I also struggled with unity but eventually decided it was too much hassle.
After Unity, as a ubuntu user, the next obvious candidate you should try is gnome-shell. Note that Unity and gnome-shell require you to re-appraise how you use your desktop which is why so many people don't like them - because they can't change and don't realise there are better ways to exploit our modern hardware.

---

### Post by Cavsfan on 2012-02-17
> **tuggy said:**
> My .02 here:

After being bored with Unity and gnome-shell (yes, I'm a die-hard gnome2 fan), I tried a few other options for a while, namely Enlightenment, XFCe and WindowMaker.

I'm now a proud WindowMaker user :D
It needs a bit of tweaking, and you wont find very modern look/feature in it, but it rocks my world at the moment :)

and here is a screenshot of my writing this post :popcorn:

[http://imgur.com/AxwEw](http://imgur.com/AxwEw)

cheers!


**Tuggy**, what version of Ubuntu are you running. Your info says Karmic Koala (testing).

---

### Post by haqking on 2012-02-17
> **Cavsfan said:**
> **Tuggy**, what version of Ubuntu are you running. Your info says Karmic Koala (testing).

I expect that is due to the fact tuggy has less than 50 posts so cant change profile ;-)

---

### Post by Cavsfan on 2012-02-17
> **haqking said:**
> I expect that is due to the fact tuggy has less than 50 posts so cant change profile ;-)

I didn't think there was a limit. If he put Karmic in there, he should be able to update it. But, only a mod would know for sure 
I guess. I've following this thread for what the options will be when 12.04 is released.

---

### Post by haqking on 2012-02-17
> **Cavsfan said:**
> I didn't think there was a limit. If he put Karmic in there, he should be able to update it. But, only a mod would know for sure 
I guess. I've following this thread for what the options will be when 12.04 is released.

[http://ubuntuforums.org/showthread.php?t=1836816](http://ubuntuforums.org/showthread.php?t=1836816)

---

### Post by cwklinuxguy on 2012-02-17
Could try E17...it's the most customizable, and can be tailored to look and act much like Gnome 2. There is also a fork of the Gnome 2 desktop called MATE.

---

### Post by @lpha on 2012-02-17
I would give Linux Mint's Cinnamon desktop a shot. They have cinnamon desktop environment and cinnamon settings, where you can get a pretty close gnome 2 replication.

It's also important to feel at home with your desktop. Here is a link to themes for the cinnamon desktop if you decide to lean towards Linux mint: [http://cinnamon-spices.linuxmint.com/themes](http://cinnamon-spices.linuxmint.com/themes)

---

### Post by tuggy on 2012-02-17
> **haqking said:**
> I expect that is due to the fact tuggy has less than 50 posts so cant change profile ;-)

hehe true, last time I used the forums it didn't have this rule of having a minimum of 50 posts.
I was in the macworld for a few years, got back to linux again, but now I can't change my profile... yet :)

---

### Post by inobe on 2012-02-17
do what we all did, try them all till you find something exceptionable :p

seriously, it isn't possible to understand your needs and pleasures

---

### Post by Cavsfan on 2012-02-18
> **Cavsfan said:**
> I didn't think there was a limit. If he put Karmic in there, he should be able to update it. But, only a mod would know for sure 
I guess. I've following this thread for what the options will be when 12.04 is released.

> **haqking said:**
> [http://ubuntuforums.org/showthread.php?t=1836816](http://ubuntuforums.org/showthread.php?t=1836816)

Thanks for the link. I didn't notice that had changed in September 2011. 
I figured if they were able to put Karmic in there, then they could change it to their new version.
Makes it confusing when someone has a screenshot of an obviously later version of Ubuntu and their info says Hardy Heron or whatever.

---

### Post by Cavsfan on 2012-02-18
> **haqking said:**
> I expect that is due to the fact tuggy has less than 50 posts so cant change profile ;-)

> **tuggy said:**
> hehe true, last time I used the forums it didn't have this rule of having a minimum of 50 posts.
I was in the macworld for a few years, got back to linux again, but now I can't change my profile... yet :)

6 more posts and you can update your version! :grin: It takes the confusion out of the picture.

---

