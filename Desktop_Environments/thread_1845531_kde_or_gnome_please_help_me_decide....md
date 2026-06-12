---
title: "kde or gnome? please help me decide..."
date: 2011-09-17
forum: Desktop Environments
---

### Post by bennypr0fane on 2011-09-17
Hello,

I guess there have been tons of pages of discussions about this topic, but i'm not trying to determine which is better here, but I'd like to piece together a system for myself that does everything I need in the way that I want it.

I installed Ubuntu on my PC 3 months ago, and coming from Windows, getting started with Gnome and setting up the applications to my liking was a basically a breeze (after clearing out some minor how-to issues with the help of wonderful people in this forum).
Then I read about **Nepomuk** and **Strigis** in KDE, which provide solutions for my dream of finding stuff on my computer, especially for my work materials where an efficient database can save me loads of search work and it would just make my life so much easier to fully implement a semantic desktop in my work.
I also learnt that I don't have to choose between Gnome and KDE, but I can just "add" KDE to Gnome and then switch from session to session or even run applications from either DE inside either of them.
So far, so great.
I installed KDE and started playing around, and I basically like the looks of it much better (but that factor is generally secondary to me). Also, Plasma in a way seems to be much more powerful, giving more direct and more integrated concept for access to modifications, tweaks and customization. That being my initial impression (not proven yet), I have considered using it exclusively. Sadly though I couldn't figure out how to perform some basic tasks with Plasma, even after quite patient research in documentation/help and forums, often finding that rather basic questions are not being answered in the documentation. I didn't succeed in finding a simple first-steps guide to PLasma desktop (mainly looked on Youtube for video tutorial, which would have been awesome).  I also got tired of posting and reposting, explaining my issues in detail, so I just went back to the already-homely Gnome and tried using KDE apps from there.

Now I'm still very unsatisfied with this solutiuon for various reasons:
- The initial speed of Ubuntu that I enjoyed so much afer installation seems lost, I'm now more reminded of the typical Windows experience with lots of waiting for things to get going.
- Especially launching KDE apps inside Gnome can take forever, but some of them (media player, IM) just work much better for me than the Gnome ones, with fewer hiccups, fewer things to fix - provided they come without the confusion that Plasma puts me into. Annoying slowdown starts with that pesky KDE wallet service demanding my password for each application!
- No **NEPOMUK** and **STRIGIS** goodness in Gnome? I also found some threads that discussed making these work in Gnome, but 1) I assume that would be tied to those very same issues I am already having? and 2) It looks like there is no proven, standard method for this combo?

So, to sum it up:

- KDE has a cooler look and *seems* to be more powerful, especially the s**emantic desktop** solution of Nepomuk still in process of being enhanced (I think). Some of the KDE apps work better for me than the Gnome ones - but that may also be true the other way round, I haven't tried most of them yet.
The downside is I have trouble getting used to Plasma desktop and the learning curve seems almost to steep for me, with much more tiresome forum posting, bugging helpful people with my questions.

- Gnome I am already comfortable with, which is a great asset to me. But some apps have shown annoying issues that also took some attention off work. Also it doesn't look as cool, and it dosen't have Nepomuk/Strigis built in.

- Combining the two seems to slow things down, taking me back to the Windows era, and it's just not a seamless, hassle-free switch. There is no switching without a restart!

What to do? Any advice is greatly appreciated. I just know Ubuntu/Linux can fulfill all my dreams as a PC user, with pro-level choices for all the tasks I need, but currently I'm at a loss of ideas. Help me out here!

---

### Post by Lars Noodén on 2011-09-17
KDE is more powerful and flexible, so if it is a choice between only the two, then it should be KDE.

However, there are other options that are quite good.  XFCE is worth looking at and LXDE is getting popular.  You can get those as part of Xubuntu-desktop and Lubuntu-desktop respectively.

---

### Post by raja.genupula on 2011-09-17
> **Lars Noodén said:**
> KDE is more powerful and flexible, so if it is a choice between only the two, then it should be KDE.

However, there are other options that are quite good.  XFCE is worth looking at and LXDE is getting popular.  You can get those as part of Xubuntu-desktop and Lubuntu-desktop respectively.

+1
yeah , as compare with ubuntu in my pc, xubuntu is very fast .

---

### Post by oldos2er on 2011-09-17
You don't mention your hardware specs; perhaps a RAM, CPU, or newer video card would help?

There's a lot of Kubuntu info here: [http://kubuntuforums.net/forums/index.php?board=13.0](http://kubuntuforums.net/forums/index.php?board=13.0)

---

### Post by josephmills on 2011-09-17
why not both ?

---

### Post by bennypr0fane on 2011-09-17
Thanks for taking the time and effort to reply everyone.
No thanks for reading only the subject. :cry: I guess I should take to posting headlines only.

---

### Post by kngts on 2011-09-17
It depends, if you want desktop with more appearance, then it's gnome.

I don't have KDE, so I don't know about that.

---

### Post by Blasphemist on 2011-09-17
check this out. I have been using this a lot lately. It is ubuntu based but uses neither gnome or kde, uses enlightenment E17. I have both g and k apps installed and everything is real fast. [http://www.bodhilinux.com/](http://www.bodhilinux.com/)

---

### Post by palz2015 on 2011-09-17
In my humble opinion, GNOME is better than KDE for everyday stuff. However, if you need a lightweight window manager, go with LXDE (Lubuntu), XFCE (Xubuntu) or even IceWM.

---

### Post by drawkcab on 2011-09-18
I'm a Gnome fan myself but I think you might prefer KDE once you know your way around.  Gnome 2.x is being replaced by Gnome 3 anyway so while it is developing and maturing it might be best to work with KDE.

---

### Post by bennypr0fane on 2011-09-18
> **oldos2er said:**
> You don't mention your hardware specs; perhaps a RAM, CPU, or newer video card would help?[/url]

I have 1GB of DDR2 RAM, CPU is AMD Athlon 64 X2 at 3,8 GHz (that's what's printed on the machine, but it's actually lower), these should suffice for running either DE nicely, right? And the graphics card may actually be kind of a weak link, but I guess it should be easily sufficient as well, it's Nvidia Gforce 6100.

> There's a lot of Kubuntu info here: [http://kubuntuforums.net/forums/index.php?board=13.0](http://kubuntuforums.net/forums/index.php?board=13.0)

thanks, I'll check it out

---

### Post by Lisiano on 2011-09-18
The reason for the slow start-up of KDE apps in Gnome is that it first needs to load some KDE libraries, true for the opposite, starting a Gnome app inside KDE means you still have to load the Gnome libraries. As long as you have something running from KDE/Gnome then the slowness shouldn't appear. Also I think you should take a look at Activity Journal ```
sudo apt-get install gnome-activity-journal
```, it uses it's own mechanism but could be something worth looking at. Also adding some more RAM could easily solve this as Linux wouldn't need to uncache the libraries from the RAM whenever it is running low.

---

### Post by bennypr0fane on 2011-09-18
> **palz2015 said:**
> In my humble opinion, GNOME is better than KDE for everyday stuff. However, if you need a lightweight window manager, go with LXDE (Lubuntu), XFCE (Xubuntu) or even IceWM.
I can't tell wether it's just down to the window manager being more lightweight, or there are other factors at play, like several parts of the software not getting along with each other.
I am guessing that my hardware, though a bit old, is sufficient
for any of the ones that come with Ubuntu, but maybe there's a way of testing that?

However, if I were to choose any different WM, would that mean I have to forfeit my current system and do a complete reinstall? If yes, is there a way of doing that without losing all the apps I installed, and account infos I already entered etc.etc.? I'd like to avoid all the extra woirk, if possible

OR could i switch to a different desktop by making some changes to my existing install?

---

### Post by bennypr0fane on 2011-09-18
In your opinion, which of the lighter window managers is more similar to Gnome in terms of Inteface and handling?

---

### Post by Lars Noodén on 2011-09-18
> **bennypr0fane said:**
> 
OR could i switch to a different desktop by making some changes to my existing install?

You can add the package "lubuntu-desktop" to add everything that is in Lubuntu.  Likewise for the package "xubuntu-desktop"   Of course you can also add just the window manager or desktop environment by itself.  FVWM-crystal is very light weight, too.

---

### Post by bennypr0fane on 2011-09-18
> **Lisiano said:**
> The reason for the slow start-up of KDE apps in Gnome is that it first needs to load some KDE libraries, true for the opposite, starting a Gnome app inside KDE means you still have to load the Gnome libraries. As long as you have something running from KDE/Gnome then the slowness shouldn't appear. Also I think you should take a look at Activity Journal ```
sudo apt-get install gnome-activity-journal
```, it uses it's own mechanism but could be something worth looking at. Also adding some more RAM could easily solve this as Linux wouldn't need to uncache the libraries from the RAM whenever it is running low.

- Thanks for the pointer! What exactly does the activity journal do?
- I wanna try to leave the hardware as it is, since my mainboard is pretty outdated and the appropriate RAM has become rather expensive
- Would it make sense to include one KDE app in the autostart so the KDE libraries would be automatically loaded at start? But that would of course increase boot time, I guess?

- What about my semantic desktop? :cry: How do i get that?

---

### Post by bennypr0fane on 2011-09-18
> **Lars Noodén said:**
> You can add the package "lubuntu-desktop" to add everything that is in Lubuntu.  Likewise for the package "xubuntu-desktop"   Of course you can also add just the window manager or desktop environment by itself.  FVWM-crystal is very light weight, too.

Maybe you already noticed: I don't know the difference between a window manager and a desktop environment. Could someone explain that to me, or direct me to a site where it is explained? That would be very helpful.

How would I install them separately?

I *can* also install just the apps I need from a different DE or (WM?), can I? OR I do I *have to* take the whole bunch of apps?  


I installed the kde package, does that mean I can keep Nepomuk/Strigis semantic desktop active in Gnome sessions?

---

### Post by Lisiano on 2011-09-18
Kubuntu (KDE) - The beast of them all, the king of customization and flashy effects. Use if you have a modern system or love being in control.
Ubuntu (Gnome) - The default and the more humble of the 4, allows you to customize most stuff but not everything, known for being the default DE on Ubuntu and for it's user-friendliness.
Xubuntu (XFCE) - The lightweight "version" of Gnome, let's you still have the customization of Gnome but you lose some of the effects Gnome can offer.
Lubuntu (LXDE) - An ever lighter "Gnome", lighter than XFCE, use if you can't use or don't like flashy effects.
Ubuntu Server Edition (CLI) - The minimalist of them all, uses the  least amount of resources than any of the above could ever achieve, use only if you love the CLI, use a server or just for giggles.
The above is straightly just my opinion.
Also as a lot of people already said, you can install any DE with any other DE, even all 4 ```
sudo apt-get install kubuntu-desktop ubuntu-desktop xubuntu-desktop lubuntu-desktop
```

And you decided to post something while I was typing. Okay.
1) I don't exactly remember, but in short, it tracks what you use during the day, programs and files and let's you search inside files, personally I don't use it since I feel like I'm being tracked. Personally I'm paranoid about leaving traces of what I do in plaintext.
2) DDR2 doesn't seem that old, as a pointer 2GB DDR3 RAM cost me 10&#8364;.
3) Probably, but put something you might actually use for example Amarok if you prefer it instead of Banshee.
4) I have no idea. But the search tools from KDE will still function, how to index though. Beats me.

Stop posting while I type! (Joking)
Windows manager - Compiz, Metacity, KDE4 Window Manager. They manage your windows, let you move them around and resize them, make them have buttons so you can close them too.
Desktop Environment - KDE, Gnome, LXDE, XFCE. Basically a compilation of software if you don't want to go into detail.

And yes you can install single apps from a different DE, BUT you will pull down some stuff from that DE (Libraries).

---

### Post by bennypr0fane on 2011-09-18
...and how do I give you guys (countable) credit/karma/kudoes or whatever for helpful answers? :grin:

Oh, I just read the forum FAQs - that's not what the beans are for.

Just know that I really appreciate people trying to help with my questions!
I hope the Q&A created here can be useful to other users as well with similar questions!

---

### Post by Lars Noodén on 2011-09-18
> **bennypr0fane said:**
> Maybe you already noticed: I don't know the difference between a window manager and a desktop environment. Could someone explain that to me, or direct me to a site where it is explained? That would be very helpful.




[http://www.tuxfiles.org/linuxhelp/xwtf.html](http://www.tuxfiles.org/linuxhelp/xwtf.html)

[http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/3/html/Reference_Guide/s1-x-clients.html](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/3/html/Reference_Guide/s1-x-clients.html)

---

### Post by Lisiano on 2011-09-18
Gawd. You love posting while I type?
Anyway.
Beans - Post count.
And for the kudos, just say Thanks and mark the thread Solved in the Thread Tools whenever it is solved. Also some day help other people that might need your help.

---

